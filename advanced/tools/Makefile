ifeq ($(SRCDIR),)
  updir = $(shell echo $(dir $(1)) | sed 's/.$$//')
  SRCDIR := $(call updir,$(CURDIR))
  BLDDIR := $(SRCDIR)
endif
SUBDIR := tools

include $(BLDDIR)/config.mk

SUBDIRS = \
  binmode-rpc-kit \
  lib \
  turbocharger \
  xml \

ifeq ($(MUST_BUILD_CLIENT),yes)
  SUBDIRS += xmlrpc xmlrpc_transport

  ifeq ($(ENABLE_CPLUSPLUS),yes)
    SUBDIRS += xml-rpc-api2cpp xml-rpc-api2txt xmlrpc_cpp_proxy

    ifeq ($(BUILD_XMLRPC_PSTREAM),yes)
      SUBDIRS += xmlrpc_pstream
    endif
  endif
endif

ifeq ($(ENABLE_CPLUSPLUS),yes)
  SUBDIRS += xmlrpc_dumpserver
endif

.PHONY: all clean distclean install uninstall check dep

all: $(SUBDIRS:%=%/all)

clean: $(SUBDIRS:%=%/clean)

distclean: $(SUBDIRS:%=%/distclean)

install: $(SUBDIRS:%=%/install)

uninstall: $(SUBDIRS:%=%/uninstall)

check:

dep: $(SUBDIRS:%=%/dep)

include $(SRCDIR)/common.mk
