REBAR ?= rebar

# workaround for a rebar bug
unexport ERL_LIBS


all: deps
	$(REBAR) compile

deps:
	mkdir -p deps; cd deps; \
		for i in ../../../deps/*; do ln -sf $$i; done
	$(REBAR) get-deps

test: test_addressbook test_json_xml

test_addressbook:
	./test


test_json_xml:
	./io_json_xml_pb addressbook.piq.pb


dialyzer: all
	dialyzer deps/*/ebin ./ebin


clean:
	$(REBAR) clean skip_deps=true
	rm -f deps/piqi_bin
	rm -f addressbook.piq.pb addressbook.pb.piq l1 l2


distclean: clean
	rm -rf ebin


.PHONY: test deps

