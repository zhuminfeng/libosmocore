# This is _NOT_ the library release version, it's an API version.
# Please read chapter "Library interface versions" of the libtool documentation
# before making any modifications: https://www.gnu.org/software/libtool/manual/html_node/Versioning.html
LIBVERSION=0:1:0

AM_CPPFLAGS = $(all_includes) -I$(top_srcdir)/include -I$(top_builddir)/include
AM_CFLAGS = -fPIC -Wall $(PCSC_CFLAGS) $(TALLOC_CFLAGS)
AM_LDFLAGS = $(COVERAGE_LDFLAGS)

if ENABLE_PCSC
# FIXME: only build the PC/SC dependent part conditional, but always build other parts

noinst_HEADERS = sim_int.h gsm_int.h

lib_LTLIBRARIES = libosmosim.la

libosmosim_la_SOURCES = core.c reader.c reader_pcsc.c class_tables.c \
			card_fs_sim.c card_fs_usim.c card_fs_uicc.c \
			card_fs_isim.c card_fs_tetra.c
libosmosim_la_LDFLAGS = -version-info $(LIBVERSION)
libosmosim_la_LIBADD = \
	$(top_builddir)/src/libosmocore.la \
	$(top_builddir)/src/gsm/libosmogsm.la \
	$(TALLOC_LIBS) \
	$(PCSC_LIBS)

endif
