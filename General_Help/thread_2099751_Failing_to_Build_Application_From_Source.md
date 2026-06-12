---
title: "Failing to Build Application From Source"
date: 2012-12-30
forum: General Help
---

### Post by texpat on 2012-12-30
Im trying to install an application called pfcalc and I'm getting stuck in the 'make' part of building it.

Terminal output after typing 'make' is:

```
Making all in src
make[1]: Entering directory `/home/texpat/Downloads/pfcalc-1.1/src'
gcc -DPACKAGE_NAME=\"pfcalc\" -DPACKAGE_TARNAME=\"pfcalc\" -DPACKAGE_VERSION=\"1.1\" -DPACKAGE_STRING=\"pfcalc\ 1.1\" -DPACKAGE_BUGREPORT=\"sargas@sdf-eu.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"pfcalc\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LOCALE_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_UNISTD_H=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -I.    -Wall -lm -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c: In function ‘printresult’:
main.c:452:8: warning: format not a string literal and no format arguments [-Wformat-security]
main.c: In function ‘setliquid’:
main.c:688:9: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result [-Wunused-result]
mv -f .deps/main.Tpo .deps/main.Po
gcc -Wall -lm -g -O2   -o pfcalc main.o  
main.o: In function `colebrook_start':
/home/texpat/Downloads/pfcalc-1.1/src/main.c:243: undefined reference to `log10'
main.o: In function `colebrook':
/home/texpat/Downloads/pfcalc-1.1/src/main.c:250: undefined reference to `log10'
/home/texpat/Downloads/pfcalc-1.1/src/main.c:250: undefined reference to `sqrt'
collect2: ld returned 1 exit status
make[1]: *** [pfcalc] Error 1
make[1]: Leaving directory `/home/texpat/Downloads/pfcalc-1.1/src'
make: *** [all-recursive] Error 
```

I suppose the "undefined reference to `log10'" and `sqrt' is an issue with missing header files. Can anyone help me with this?

Thanks for reading. I appreciate any hints and pointers.
Tx

---

### Post by thnewguy on 2012-12-30
Try adding the line
```

#include <math.h>

```
to the top of the "src/main.c" file. Both the log10 and the sqrt functions are included in the math header file. You should probably contact the author of the software and inform them of the error message.

---

### Post by steeldriver on 2012-12-30
AFAIK header files don't have anything to do with 

```
undefined reference
```errors - things are only *declared *in header files (they are *defined *in libraries or object files, which are incorporated by the linker)

Your issue is probably the order in which the libraries are being linked - some (earlier?) versions of gcc allowed relaxed ordering by default, but I believe that now (in order to prevent a lot of recursive symbol resolution) the default is to require libraries to be linked in the order of symbol usage i.e. if library (or object file) A uses symbols from library B then A has to be to the left of B on the link line

In your particular case, it looks like the math library (-lm) is listed ahead of 'main.o' - it likely needs to go after it

```
-Wall [COLOR=Red]-lm[/COLOR] -g -O2 -MT [COLOR=Red]main.o[/COLOR]
``````
-Wall -g -O2 -MT [COLOR=Red]main.o -lm[/COLOR] 
```[As an aside, I suspect the makefile is a bit of a mess because it seems to have the compile phase and link phase flags all mixed up together]

---

### Post by texpat on 2012-12-30
> **thnewguy said:**
> Try adding the line
```

#include <math.h>

```
to the top of the "src/main.c" file. Both the log10 and the sqrt functions are included in the math header file. You should probably contact the author of the software and inform them of the error message.

This is what I actually thought the problem would be. But it turns out that math.h is included, albeit not directly in main.c, which contains [FONT="Courier New"]**#include <main.h>**[/FONT].
[FONT="Courier New"]**math.h**[/FONT] is then included in [FONT="Courier New"]**main.h**[/FONT].

---

### Post by texpat on 2012-12-30
> **steeldriver said:**
> AFAIK header files don't have anything to do with 

```
undefined reference
```errors - things are only *declared *in header files (they are *defined *in libraries or object files, which are incorporated by the linker)

Your issue is probably the order in which the libraries are being linked - some (earlier?) versions of gcc allowed relaxed ordering by default, but I believe that now (in order to prevent a lot of recursive symbol resolution) the default is to require libraries to be linked in the order of symbol usage i.e. if library (or object file) A uses symbols from library B then A has to be to the left of B on the link line

In your particular case, it looks like the math library (-lm) is listed ahead of 'main.o' - it likely needs to go after it

```
-Wall [COLOR=Red]-lm[/COLOR] -g -O2 -MT [COLOR=Red]main.o[/COLOR]
``````
-Wall -g -O2 -MT [COLOR=Red]main.o -lm[/COLOR] 
```[As an aside, I suspect the makefile is a bit of a mess because it seems to have the compile phase and link phase flags all mixed up together]

I'm afraid I'm out of my depth here. I never did much programming (C or otherwise) and that's decades ago.

I (think) I can follow up to > ...linked in the order of symbol usage i.e. if library (or object file) A uses symbols from library B then A has to be to the left of B on the link line

Following that it seems you suggest a fix. Where would that be applied?

---

### Post by MG&amp;TL on 2012-12-30
Can you post the contents of the file called "Makefile" in the top directory please? :)

---

### Post by texpat on 2012-12-30
> **MG&TL said:**
> Can you post the contents of the file called "Makefile" in the top directory please? :)
Happy to oblige:

```
# Makefile.in generated by automake 1.11.4 from Makefile.am.
# Makefile.  Generated from Makefile.in by configure.

# Copyright (C) 1994, 1995, 1996, 1997, 1998, 1999, 2000, 2001, 2002,
# 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010, 2011 Free Software
# Foundation, Inc.
# This Makefile.in is free software; the Free Software Foundation
# gives unlimited permission to copy and/or distribute it,
# with or without modifications, as long as this notice is preserved.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY, to the extent permitted by law; without
# even the implied warranty of MERCHANTABILITY or FITNESS FOR A
# PARTICULAR PURPOSE.



am__make_dryrun = \
  { \
    am__dry=no; \
    case $$MAKEFLAGS in \
      *\\[\ \	]*) \
        echo 'am--echo: ; @echo "AM"  OK' | $(MAKE) -f - 2>/dev/null \
          | grep '^AM OK$$' >/dev/null || am__dry=yes;; \
      *) \
        for am__flg in $$MAKEFLAGS; do \
          case $$am__flg in \
            *=*|--*) ;; \
            *n*) am__dry=yes; break;; \
          esac; \
        done;; \
    esac; \
    test $$am__dry = yes; \
  }
pkgdatadir = $(datadir)/pfcalc
pkgincludedir = $(includedir)/pfcalc
pkglibdir = $(libdir)/pfcalc
pkglibexecdir = $(libexecdir)/pfcalc
am__cd = CDPATH="$${ZSH_VERSION+.}$(PATH_SEPARATOR)" && cd
install_sh_DATA = $(install_sh) -c -m 644
install_sh_PROGRAM = $(install_sh) -c
install_sh_SCRIPT = $(install_sh) -c
INSTALL_HEADER = $(INSTALL_DATA)
transform = $(program_transform_name)
NORMAL_INSTALL = :
PRE_INSTALL = :
POST_INSTALL = :
NORMAL_UNINSTALL = :
PRE_UNINSTALL = :
POST_UNINSTALL = :
subdir = .
DIST_COMMON = $(am__configure_deps) $(srcdir)/Makefile.am \
	$(srcdir)/Makefile.in $(top_srcdir)/configure depcomp \
	install-sh missing
ACLOCAL_M4 = $(top_srcdir)/aclocal.m4
am__aclocal_m4_deps = $(top_srcdir)/configure.ac
am__configure_deps = $(am__aclocal_m4_deps) $(CONFIGURE_DEPENDENCIES) \
	$(ACLOCAL_M4)
am__CONFIG_DISTCLEAN_FILES = config.status config.cache config.log \
 configure.lineno config.status.lineno
mkinstalldirs = $(install_sh) -d
CONFIG_CLEAN_FILES =
CONFIG_CLEAN_VPATH_FILES =
SOURCES =
DIST_SOURCES =
RECURSIVE_TARGETS = all-recursive check-recursive dvi-recursive \
	html-recursive info-recursive install-data-recursive \
	install-dvi-recursive install-exec-recursive \
	install-html-recursive install-info-recursive \
	install-pdf-recursive install-ps-recursive install-recursive \
	installcheck-recursive installdirs-recursive pdf-recursive \
	ps-recursive uninstall-recursive
am__can_run_installinfo = \
  case $$AM_UPDATE_INFO_DIR in \
    n|no|NO) false;; \
    *) (install-info --version) >/dev/null 2>&1;; \
  esac
RECURSIVE_CLEAN_TARGETS = mostlyclean-recursive clean-recursive	\
  distclean-recursive maintainer-clean-recursive
AM_RECURSIVE_TARGETS = $(RECURSIVE_TARGETS:-recursive=) \
	$(RECURSIVE_CLEAN_TARGETS:-recursive=) tags TAGS ctags CTAGS \
	distdir dist dist-all distcheck
ETAGS = etags
CTAGS = ctags
DIST_SUBDIRS = $(SUBDIRS)
DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
distdir = $(PACKAGE)-$(VERSION)
top_distdir = $(distdir)
am__remove_distdir = \
  if test -d "$(distdir)"; then \
    find "$(distdir)" -type d ! -perm -200 -exec chmod u+w {} ';' \
      && rm -rf "$(distdir)" \
      || { sleep 5 && rm -rf "$(distdir)"; }; \
  else :; fi
am__relativize = \
  dir0=`pwd`; \
  sed_first='s,^\([^/]*\)/.*$$,\1,'; \
  sed_rest='s,^[^/]*/*,,'; \
  sed_last='s,^.*/\([^/]*\)$$,\1,'; \
  sed_butlast='s,/*[^/]*$$,,'; \
  while test -n "$$dir1"; do \
    first=`echo "$$dir1" | sed -e "$$sed_first"`; \
    if test "$$first" != "."; then \
      if test "$$first" = ".."; then \
        dir2=`echo "$$dir0" | sed -e "$$sed_last"`/"$$dir2"; \
        dir0=`echo "$$dir0" | sed -e "$$sed_butlast"`; \
      else \
        first2=`echo "$$dir2" | sed -e "$$sed_first"`; \
        if test "$$first2" = "$$first"; then \
          dir2=`echo "$$dir2" | sed -e "$$sed_rest"`; \
        else \
          dir2="../$$dir2"; \
        fi; \
        dir0="$$dir0"/"$$first"; \
      fi; \
    fi; \
    dir1=`echo "$$dir1" | sed -e "$$sed_rest"`; \
  done; \
  reldir="$$dir2"
DIST_ARCHIVES = $(distdir).tar.gz
GZIP_ENV = --best
distuninstallcheck_listfiles = find . -type f -print
am__distuninstallcheck_listfiles = $(distuninstallcheck_listfiles) \
  | sed 's|^\./|$(prefix)/|' | grep -v '$(infodir)/dir$$'
distcleancheck_listfiles = find . -type f -print
ACLOCAL = ${SHELL} /home/texpat/Downloads/pfcalc-1.1/missing --run aclocal-1.11
AMTAR = $${TAR-tar}
AUTOCONF = ${SHELL} /home/texpat/Downloads/pfcalc-1.1/missing --run autoconf
AUTOHEADER = ${SHELL} /home/texpat/Downloads/pfcalc-1.1/missing --run autoheader
AUTOMAKE = ${SHELL} /home/texpat/Downloads/pfcalc-1.1/missing --run automake-1.11
AWK = mawk
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2
CPP = gcc -E
CPPFLAGS = 
CYGPATH_W = echo
DEFS = -DPACKAGE_NAME=\"pfcalc\" -DPACKAGE_TARNAME=\"pfcalc\" -DPACKAGE_VERSION=\"1.1\" -DPACKAGE_STRING=\"pfcalc\ 1.1\" -DPACKAGE_BUGREPORT=\"sargas@sdf-eu.org\" -DPACKAGE_URL=\"\" -DPACKAGE=\"pfcalc\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LOCALE_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_UNISTD_H=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1
DEPDIR = .deps
ECHO_C = 
ECHO_N = -n
ECHO_T = 
EGREP = /bin/grep -E
EXEEXT = 
GREP = /bin/grep
INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = $(install_sh) -c -s
LDFLAGS = 
LIBOBJS = 
LIBS = 
LTLIBOBJS = 
MAKEINFO = ${SHELL} /home/texpat/Downloads/pfcalc-1.1/missing --run makeinfo
MKDIR_P = /bin/mkdir -p
OBJEXT = o
PACKAGE = pfcalc
PACKAGE_BUGREPORT = sargas@sdf-eu.org
PACKAGE_NAME = pfcalc
PACKAGE_STRING = pfcalc 1.1
PACKAGE_TARNAME = pfcalc
PACKAGE_URL = 
PACKAGE_VERSION = 1.1
PATH_SEPARATOR = :
SET_MAKE = 
SHELL = /bin/bash
STRIP = 
VERSION = 1.1
abs_builddir = /home/texpat/Downloads/pfcalc-1.1
abs_srcdir = /home/texpat/Downloads/pfcalc-1.1
abs_top_builddir = /home/texpat/Downloads/pfcalc-1.1
abs_top_srcdir = /home/texpat/Downloads/pfcalc-1.1
ac_ct_CC = gcc
am__include = include
am__leading_dot = .
am__quote = 
am__tar = $${TAR-tar} chof - "$$tardir"
am__untar = $${TAR-tar} xf -
bindir = ${exec_prefix}/bin
build_alias = 
builddir = .
datadir = ${datarootdir}
datarootdir = ${prefix}/share
docdir = ${datarootdir}/doc/${PACKAGE_TARNAME}
dvidir = ${docdir}
exec_prefix = ${prefix}
host_alias = 
htmldir = ${docdir}
includedir = ${prefix}/include
infodir = ${datarootdir}/info
install_sh = ${SHELL} /home/texpat/Downloads/pfcalc-1.1/install-sh
libdir = ${exec_prefix}/lib
libexecdir = ${exec_prefix}/libexec
localedir = ${datarootdir}/locale
localstatedir = ${prefix}/var
mandir = ${datarootdir}/man
mkdir_p = /bin/mkdir -p
oldincludedir = /usr/include
pdfdir = ${docdir}
prefix = /usr/local
program_transform_name = s,x,x,
psdir = ${docdir}
sbindir = ${exec_prefix}/sbin
sharedstatedir = ${prefix}/com
srcdir = .
sysconfdir = ${prefix}/etc
target_alias = 
top_build_prefix = 
top_builddir = .
top_srcdir = .
AUTOMAKE_OPTIONS = foreign
SUBDIRS = src scripts doc data man
all: all-recursive

.SUFFIXES:
am--refresh: Makefile
	@:
$(srcdir)/Makefile.in:  $(srcdir)/Makefile.am  $(am__configure_deps)
	@for dep in $?; do \
	  case '$(am__configure_deps)' in \
	    *$$dep*) \
	      echo ' cd $(srcdir) && $(AUTOMAKE) --foreign'; \
	      $(am__cd) $(srcdir) && $(AUTOMAKE) --foreign \
		&& exit 0; \
	      exit 1;; \
	  esac; \
	done; \
	echo ' cd $(top_srcdir) && $(AUTOMAKE) --foreign Makefile'; \
	$(am__cd) $(top_srcdir) && \
	  $(AUTOMAKE) --foreign Makefile
.PRECIOUS: Makefile
Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
	@case '$?' in \
	  *config.status*) \
	    echo ' $(SHELL) ./config.status'; \
	    $(SHELL) ./config.status;; \
	  *) \
	    echo ' cd $(top_builddir) && $(SHELL) ./config.status $@ $(am__depfiles_maybe)'; \
	    cd $(top_builddir) && $(SHELL) ./config.status $@ $(am__depfiles_maybe);; \
	esac;

$(top_builddir)/config.status: $(top_srcdir)/configure $(CONFIG_STATUS_DEPENDENCIES)
	$(SHELL) ./config.status --recheck

$(top_srcdir)/configure:  $(am__configure_deps)
	$(am__cd) $(srcdir) && $(AUTOCONF)
$(ACLOCAL_M4):  $(am__aclocal_m4_deps)
	$(am__cd) $(srcdir) && $(ACLOCAL) $(ACLOCAL_AMFLAGS)
$(am__aclocal_m4_deps):

# This directory's subdirectories are mostly independent; you can cd
# into them and run `make' without going through this Makefile.
# To change the values of `make' variables: instead of editing Makefiles,
# (1) if the variable is set in `config.status', edit `config.status'
#     (which will cause the Makefiles to be regenerated when you run `make');
# (2) otherwise, pass the desired values on the `make' command line.
$(RECURSIVE_TARGETS):
	@fail= failcom='exit 1'; \
	for f in x $$MAKEFLAGS; do \
	  case $$f in \
	    *=* | --[!k]*);; \
	    *k*) failcom='fail=yes';; \
	  esac; \
	done; \
	dot_seen=no; \
	target=`echo $@ | sed s/-recursive//`; \
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  echo "Making $$target in $$subdir"; \
	  if test "$$subdir" = "."; then \
	    dot_seen=yes; \
	    local_target="$$target-am"; \
	  else \
	    local_target="$$target"; \
	  fi; \
	  ($(am__cd) $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
	  || eval $$failcom; \
	done; \
	if test "$$dot_seen" = "no"; then \
	  $(MAKE) $(AM_MAKEFLAGS) "$$target-am" || exit 1; \
	fi; test -z "$$fail"

$(RECURSIVE_CLEAN_TARGETS):
	@fail= failcom='exit 1'; \
	for f in x $$MAKEFLAGS; do \
	  case $$f in \
	    *=* | --[!k]*);; \
	    *k*) failcom='fail=yes';; \
	  esac; \
	done; \
	dot_seen=no; \
	case "$@" in \
	  distclean-* | maintainer-clean-*) list='$(DIST_SUBDIRS)' ;; \
	  *) list='$(SUBDIRS)' ;; \
	esac; \
	rev=''; for subdir in $$list; do \
	  if test "$$subdir" = "."; then :; else \
	    rev="$$subdir $$rev"; \
	  fi; \
	done; \
	rev="$$rev ."; \
	target=`echo $@ | sed s/-recursive//`; \
	for subdir in $$rev; do \
	  echo "Making $$target in $$subdir"; \
	  if test "$$subdir" = "."; then \
	    local_target="$$target-am"; \
	  else \
	    local_target="$$target"; \
	  fi; \
	  ($(am__cd) $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
	  || eval $$failcom; \
	done && test -z "$$fail"
tags-recursive:
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  test "$$subdir" = . || ($(am__cd) $$subdir && $(MAKE) $(AM_MAKEFLAGS) tags); \
	done
ctags-recursive:
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  test "$$subdir" = . || ($(am__cd) $$subdir && $(MAKE) $(AM_MAKEFLAGS) ctags); \
	done

ID: $(HEADERS) $(SOURCES) $(LISP) $(TAGS_FILES)
	list='$(SOURCES) $(HEADERS) $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	mkid -fID $$unique
tags: TAGS

TAGS: tags-recursive $(HEADERS) $(SOURCES)  $(TAGS_DEPENDENCIES) \
		$(TAGS_FILES) $(LISP)
	set x; \
	here=`pwd`; \
	if ($(ETAGS) --etags-include --version) >/dev/null 2>&1; then \
	  include_option=--etags-include; \
	  empty_fix=.; \
	else \
	  include_option=--include; \
	  empty_fix=; \
	fi; \
	list='$(SUBDIRS)'; for subdir in $$list; do \
	  if test "$$subdir" = .; then :; else \
	    test ! -f $$subdir/TAGS || \
	      set "$$@" "$$include_option=$$here/$$subdir/TAGS"; \
	  fi; \
	done; \
	list='$(SOURCES) $(HEADERS)  $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	shift; \
	if test -z "$(ETAGS_ARGS)$$*$$unique"; then :; else \
	  test -n "$$unique" || unique=$$empty_fix; \
	  if test $$# -gt 0; then \
	    $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
	      "$$@" $$unique; \
	  else \
	    $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
	      $$unique; \
	  fi; \
	fi
ctags: CTAGS
CTAGS: ctags-recursive $(HEADERS) $(SOURCES)  $(TAGS_DEPENDENCIES) \
		$(TAGS_FILES) $(LISP)
	list='$(SOURCES) $(HEADERS)  $(LISP) $(TAGS_FILES)'; \
	unique=`for i in $$list; do \
	    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
	  done | \
	  $(AWK) '{ files[$$0] = 1; nonempty = 1; } \
	      END { if (nonempty) { for (i in files) print i; }; }'`; \
	test -z "$(CTAGS_ARGS)$$unique" \
	  || $(CTAGS) $(CTAGSFLAGS) $(AM_CTAGSFLAGS) $(CTAGS_ARGS) \
	     $$unique

GTAGS:
	here=`$(am__cd) $(top_builddir) && pwd` \
	  && $(am__cd) $(top_srcdir) \
	  && gtags -i $(GTAGS_ARGS) "$$here"

distclean-tags:
	-rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags

distdir: $(DISTFILES)
	$(am__remove_distdir)
	test -d "$(distdir)" || mkdir "$(distdir)"
	@srcdirstrip=`echo "$(srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
	topsrcdirstrip=`echo "$(top_srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
	list='$(DISTFILES)'; \
	  dist_files=`for file in $$list; do echo $$file; done | \
	  sed -e "s|^$$srcdirstrip/||;t" \
	      -e "s|^$$topsrcdirstrip/|$(top_builddir)/|;t"`; \
	case $$dist_files in \
	  */*) $(MKDIR_P) `echo "$$dist_files" | \
			   sed '/\//!d;s|^|$(distdir)/|;s,/[^/]*$$,,' | \
			   sort -u` ;; \
	esac; \
	for file in $$dist_files; do \
	  if test -f $$file || test -d $$file; then d=.; else d=$(srcdir); fi; \
	  if test -d $$d/$$file; then \
	    dir=`echo "/$$file" | sed -e 's,/[^/]*$$,,'`; \
	    if test -d "$(distdir)/$$file"; then \
	      find "$(distdir)/$$file" -type d ! -perm -700 -exec chmod u+rwx {} \;; \
	    fi; \
	    if test -d $(srcdir)/$$file && test $$d != $(srcdir); then \
	      cp -fpR $(srcdir)/$$file "$(distdir)$$dir" || exit 1; \
	      find "$(distdir)/$$file" -type d ! -perm -700 -exec chmod u+rwx {} \;; \
	    fi; \
	    cp -fpR $$d/$$file "$(distdir)$$dir" || exit 1; \
	  else \
	    test -f "$(distdir)/$$file" \
	    || cp -p $$d/$$file "$(distdir)/$$file" \
	    || exit 1; \
	  fi; \
	done
	@list='$(DIST_SUBDIRS)'; for subdir in $$list; do \
	  if test "$$subdir" = .; then :; else \
	    $(am__make_dryrun) \
	      || test -d "$(distdir)/$$subdir" \
	      || $(MKDIR_P) "$(distdir)/$$subdir" \
	      || exit 1; \
	    dir1=$$subdir; dir2="$(distdir)/$$subdir"; \
	    $(am__relativize); \
	    new_distdir=$$reldir; \
	    dir1=$$subdir; dir2="$(top_distdir)"; \
	    $(am__relativize); \
	    new_top_distdir=$$reldir; \
	    echo " (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) top_distdir="$$new_top_distdir" distdir="$$new_distdir" \\"; \
	    echo "     am__remove_distdir=: am__skip_length_check=: am__skip_mode_fix=: distdir)"; \
	    ($(am__cd) $$subdir && \
	      $(MAKE) $(AM_MAKEFLAGS) \
	        top_distdir="$$new_top_distdir" \
	        distdir="$$new_distdir" \
		am__remove_distdir=: \
		am__skip_length_check=: \
		am__skip_mode_fix=: \
	        distdir) \
	      || exit 1; \
	  fi; \
	done
	-test -n "$(am__skip_mode_fix)" \
	|| find "$(distdir)" -type d ! -perm -755 \
		-exec chmod u+rwx,go+rx {} \; -o \
	  ! -type d ! -perm -444 -links 1 -exec chmod a+r {} \; -o \
	  ! -type d ! -perm -400 -exec chmod a+r {} \; -o \
	  ! -type d ! -perm -444 -exec $(install_sh) -c -m a+r {} {} \; \
	|| chmod -R a+r "$(distdir)"
dist-gzip: distdir
	tardir=$(distdir) && $(am__tar) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).tar.gz
	$(am__remove_distdir)

dist-bzip2: distdir
	tardir=$(distdir) && $(am__tar) | BZIP2=$${BZIP2--9} bzip2 -c >$(distdir).tar.bz2
	$(am__remove_distdir)

dist-lzip: distdir
	tardir=$(distdir) && $(am__tar) | lzip -c $${LZIP_OPT--9} >$(distdir).tar.lz
	$(am__remove_distdir)

dist-lzma: distdir
	tardir=$(distdir) && $(am__tar) | lzma -9 -c >$(distdir).tar.lzma
	$(am__remove_distdir)

dist-xz: distdir
	tardir=$(distdir) && $(am__tar) | XZ_OPT=$${XZ_OPT--e} xz -c >$(distdir).tar.xz
	$(am__remove_distdir)

dist-tarZ: distdir
	tardir=$(distdir) && $(am__tar) | compress -c >$(distdir).tar.Z
	$(am__remove_distdir)

dist-shar: distdir
	shar $(distdir) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).shar.gz
	$(am__remove_distdir)

dist-zip: distdir
	-rm -f $(distdir).zip
	zip -rq $(distdir).zip $(distdir)
	$(am__remove_distdir)

dist dist-all: distdir
	tardir=$(distdir) && $(am__tar) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).tar.gz
	$(am__remove_distdir)

# This target untars the dist file and tries a VPATH configuration.  Then
# it guarantees that the distribution is self-contained by making another
# tarfile.
distcheck: dist
	case '$(DIST_ARCHIVES)' in \
	*.tar.gz*) \
	  GZIP=$(GZIP_ENV) gzip -dc $(distdir).tar.gz | $(am__untar) ;;\
	*.tar.bz2*) \
	  bzip2 -dc $(distdir).tar.bz2 | $(am__untar) ;;\
	*.tar.lzma*) \
	  lzma -dc $(distdir).tar.lzma | $(am__untar) ;;\
	*.tar.lz*) \
	  lzip -dc $(distdir).tar.lz | $(am__untar) ;;\
	*.tar.xz*) \
	  xz -dc $(distdir).tar.xz | $(am__untar) ;;\
	*.tar.Z*) \
	  uncompress -c $(distdir).tar.Z | $(am__untar) ;;\
	*.shar.gz*) \
	  GZIP=$(GZIP_ENV) gzip -dc $(distdir).shar.gz | unshar ;;\
	*.zip*) \
	  unzip $(distdir).zip ;;\
	esac
	chmod -R a-w $(distdir); chmod a+w $(distdir)
	mkdir $(distdir)/_build
	mkdir $(distdir)/_inst
	chmod a-w $(distdir)
	test -d $(distdir)/_build || exit 0; \
	dc_install_base=`$(am__cd) $(distdir)/_inst && pwd | sed -e 's,^[^:\\/]:[\\/],/,'` \
	  && dc_destdir="$${TMPDIR-/tmp}/am-dc-$$$$/" \
	  && am__cwd=`pwd` \
	  && $(am__cd) $(distdir)/_build \
	  && ../configure --srcdir=.. --prefix="$$dc_install_base" \
	    $(AM_DISTCHECK_CONFIGURE_FLAGS) \
	    $(DISTCHECK_CONFIGURE_FLAGS) \
	  && $(MAKE) $(AM_MAKEFLAGS) \
	  && $(MAKE) $(AM_MAKEFLAGS) dvi \
	  && $(MAKE) $(AM_MAKEFLAGS) check \
	  && $(MAKE) $(AM_MAKEFLAGS) install \
	  && $(MAKE) $(AM_MAKEFLAGS) installcheck \
	  && $(MAKE) $(AM_MAKEFLAGS) uninstall \
	  && $(MAKE) $(AM_MAKEFLAGS) distuninstallcheck_dir="$$dc_install_base" \
	        distuninstallcheck \
	  && chmod -R a-w "$$dc_install_base" \
	  && ({ \
	       (cd ../.. && umask 077 && mkdir "$$dc_destdir") \
	       && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" install \
	       && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" uninstall \
	       && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" \
	            distuninstallcheck_dir="$$dc_destdir" distuninstallcheck; \
	      } || { rm -rf "$$dc_destdir"; exit 1; }) \
	  && rm -rf "$$dc_destdir" \
	  && $(MAKE) $(AM_MAKEFLAGS) dist \
	  && rm -rf $(DIST_ARCHIVES) \
	  && $(MAKE) $(AM_MAKEFLAGS) distcleancheck \
	  && cd "$$am__cwd" \
	  || exit 1
	$(am__remove_distdir)
	@(echo "$(distdir) archives ready for distribution: "; \
	  list='$(DIST_ARCHIVES)'; for i in $$list; do echo $$i; done) | \
	  sed -e 1h -e 1s/./=/g -e 1p -e 1x -e '$$p' -e '$$x'
distuninstallcheck:
	@test -n '$(distuninstallcheck_dir)' || { \
	  echo 'ERROR: trying to run $@ with an empty' \
	       '$$(distuninstallcheck_dir)' >&2; \
	  exit 1; \
	}; \
	$(am__cd) '$(distuninstallcheck_dir)' || { \
	  echo 'ERROR: cannot chdir into $(distuninstallcheck_dir)' >&2; \
	  exit 1; \
	}; \
	test `$(am__distuninstallcheck_listfiles) | wc -l` -eq 0 \
	   || { echo "ERROR: files left after uninstall:" ; \
	        if test -n "$(DESTDIR)"; then \
	          echo "  (check DESTDIR support)"; \
	        fi ; \
	        $(distuninstallcheck_listfiles) ; \
	        exit 1; } >&2
distcleancheck: distclean
	@if test '$(srcdir)' = . ; then \
	  echo "ERROR: distcleancheck can only run from a VPATH build" ; \
	  exit 1 ; \
	fi
	@test `$(distcleancheck_listfiles) | wc -l` -eq 0 \
	  || { echo "ERROR: files left in build directory after distclean:" ; \
	       $(distcleancheck_listfiles) ; \
	       exit 1; } >&2
check-am: all-am
check: check-recursive
all-am: Makefile
installdirs: installdirs-recursive
installdirs-am:
install: install-recursive
install-exec: install-exec-recursive
install-data: install-data-recursive
uninstall: uninstall-recursive

install-am: all-am
	@$(MAKE) $(AM_MAKEFLAGS) install-exec-am install-data-am

installcheck: installcheck-recursive
install-strip:
	if test -z '$(STRIP)'; then \
	  $(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
	    install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
	      install; \
	else \
	  $(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
	    install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
	    "INSTALL_PROGRAM_ENV=STRIPPROG='$(STRIP)'" install; \
	fi
mostlyclean-generic:

clean-generic:

distclean-generic:
	-test -z "$(CONFIG_CLEAN_FILES)" || rm -f $(CONFIG_CLEAN_FILES)
	-test . = "$(srcdir)" || test -z "$(CONFIG_CLEAN_VPATH_FILES)" || rm -f $(CONFIG_CLEAN_VPATH_FILES)

maintainer-clean-generic:
	@echo "This command is intended for maintainers to use"
	@echo "it deletes files that may require special tools to rebuild."
clean: clean-recursive

clean-am: clean-generic mostlyclean-am

distclean: distclean-recursive
	-rm -f $(am__CONFIG_DISTCLEAN_FILES)
	-rm -f Makefile
distclean-am: clean-am distclean-generic distclean-tags

dvi: dvi-recursive

dvi-am:

html: html-recursive

html-am:

info: info-recursive

info-am:

install-data-am:

install-dvi: install-dvi-recursive

install-dvi-am:

install-exec-am:

install-html: install-html-recursive

install-html-am:

install-info: install-info-recursive

install-info-am:

install-man:

install-pdf: install-pdf-recursive

install-pdf-am:

install-ps: install-ps-recursive

install-ps-am:

installcheck-am:

maintainer-clean: maintainer-clean-recursive
	-rm -f $(am__CONFIG_DISTCLEAN_FILES)
	-rm -rf $(top_srcdir)/autom4te.cache
	-rm -f Makefile
maintainer-clean-am: distclean-am maintainer-clean-generic

mostlyclean: mostlyclean-recursive

mostlyclean-am: mostlyclean-generic

pdf: pdf-recursive

pdf-am:

ps: ps-recursive

ps-am:

uninstall-am:

.MAKE: $(RECURSIVE_CLEAN_TARGETS) $(RECURSIVE_TARGETS) ctags-recursive \
	install-am install-strip tags-recursive

.PHONY: $(RECURSIVE_CLEAN_TARGETS) $(RECURSIVE_TARGETS) CTAGS GTAGS \
	all all-am am--refresh check check-am clean clean-generic \
	ctags ctags-recursive dist dist-all dist-bzip2 dist-gzip \
	dist-lzip dist-lzma dist-shar dist-tarZ dist-xz dist-zip \
	distcheck distclean distclean-generic distclean-tags \
	distcleancheck distdir distuninstallcheck dvi dvi-am html \
	html-am info info-am install install-am install-data \
	install-data-am install-dvi install-dvi-am install-exec \
	install-exec-am install-html install-html-am install-info \
	install-info-am install-man install-pdf install-pdf-am \
	install-ps install-ps-am install-strip installcheck \
	installcheck-am installdirs installdirs-am maintainer-clean \
	maintainer-clean-generic mostlyclean mostlyclean-generic pdf \
	pdf-am ps ps-am tags tags-recursive uninstall uninstall-am


# Tell versions [3.59,3.63) of GNU make to not export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
```

---

### Post by MG&amp;TL on 2012-12-30
Agh. Autoconf. ](*,)

Sorry, that's a generated makefile, can you post Makefile.am please?

---

### Post by texpat on 2012-12-30
> **MG&TL said:**
> Agh. Autoconf. ](*,)

Sorry, that's a generated makefile, can you post Makefile.am please?

OK, not sure this is of much use, though:

```
AUTOMAKE_OPTIONS = foreign
SUBDIRS = src scripts doc data man
```

Looks like there's a whole bunch of stuff elsewhere (SUBDIRS).

---

### Post by MG&amp;TL on 2012-12-30
> **texpat said:**
> OK, not sure this is of much use, though:

```
AUTOMAKE_OPTIONS = foreign
SUBDIRS = src scripts doc data man
```

Looks like there's a whole bunch of stuff elsewhere (SUBDIRS).

Oh lordy. Do you mind posting where you got this from? I'll see if I can get anything working. 

[Obligatory autoconf rant.]("http://freecode.com/articles/stop-the-autoconf-insanity-why-we-need-a-new-build-system")

---

### Post by mc4man on 2012-12-30
Worst case if you can't square up source - 
Install gcc-4.4
clean your source or start fresh, configure with 

```
CC=gcc-4.4 ./configure
```

---

### Post by texpat on 2012-12-30
> **MG&TL said:**
> Oh lordy. Do you mind posting where you got this from? I'll see if I can get anything working. 

[Obligatory autoconf rant.]("http://freecode.com/articles/stop-the-autoconf-insanity-why-we-need-a-new-build-system")

I got this from Sourceforge at: [http://sourceforge.net/projects/pfcalc/files/pfcalc/1.1/pfcalc-1.1.tar.gz/download](http://sourceforge.net/projects/pfcalc/files/pfcalc/1.1/pfcalc-1.1.tar.gz/download)

I've emailed the problem to the developer/maintainer, too, btw.

---

### Post by MG&amp;TL on 2012-12-30
> **texpat said:**
> I got this from Sourceforge at: [http://sourceforge.net/projects/pfcalc/files/pfcalc/1.1/pfcalc-1.1.tar.gz/download](http://sourceforge.net/projects/pfcalc/files/pfcalc/1.1/pfcalc-1.1.tar.gz/download)

I've emailed the problem to the developer/maintainer, too, btw.

Well, while the maintainer does their thing, I made a fairly simple workaround:

1. Change directory into the src/ directory.
2. Enter the following command:

```
cc -o pfcalc main.c -lm

```

You'll get one or two warnings, but it should compile successfully.

3. Run the binary as per usual from that directory. Example:

```
michael@michael-desktop:~/Downloads/pfcalc-1.1/src$ ./pfcalc 

	pfcalc version 1.1
	Copyright (C) 2009-2012 sargas@sdf-eu.org
	Distributed under the GNU General Public License v3.0 or later

	pfcalc computes pressure loss using the Darcy-Weisbach equation.
	Usage:
		pfcalc [ -viotkzKmruehV ] -dfl
	Where:
		-v or --verbose       enable verbose operation
		-d or --diameter      set hydraulic diameter in mm
		-l or --length        set pipe length in m
		-f or --flow-rate     set flow through pipe in m3/h
		-t or --temperature   set temperature - default 20 degrees C
		-k or --roughness     set pipe roughness - default 4.57e-2 mm
		-K or --K-factor      set K-factor - default 0
		-L or --equiv-length  set equivalent length - default 0
		-z or --elevation     set elevation - default 0 m
		-m or --medium        set working medium - default water
		-r or --density       set density - default 1000 kg/m3
		-u or --viscosity     set viscosity - default 1.56e-6 m2/s
		-g or --gravity       set gravity const. - default 9.80665 m/s2
		-e or --tolerance     set tolerance - default 1e-5
		-i or --input         input data from csv file
		-o or --output        output result to csv file
		-V or --version       print version and exit
		-h or --help          display this screen and exit
	See manual for more information.
	Home page: <http://pfcalc.sf.net>
     
michael@michael-desktop:~/Downloads/pfcalc-1.1/src$ ./pfcalc -i ../data/test.csv 
d[mm]   l[m]    Q[m3/h] v[m/s]  Re[-]   fr[-]   hs[bar] ml[bar] Ml[bar] Tl[bar]
--------------------------------------------------------------------------------
17.3    1       50      59.086  1E+06   0.02539 0.97901 0       25.571  26.55   
22.3    1       50      35.561  7.9E+05 0.02379 0.97901 0       6.7331  7.7121  
28.5    1       50      21.771  6.2E+05 0.02244 0.97901 0       1.8628  2.8418  
37.2    1       50      12.779  4.7E+05 0.02119 0.97901 0       0.46433 1.4433  
43.1    1       50      9.5197  4.1E+05 0.0206  0.97901 0       0.21624 1.1953  
54.5    1       50      5.9537  3.2E+05 0.01982 0.97901 0       0.06436 1.0434  
70.3    1       50      3.5782  2.5E+05 0.01922 0.97901 0       0.01747 0.99649 
82.5    1       50      2.5982  2.1E+05 0.01897 0.97901 0       0.00775 0.98676 
107.1   1       50      1.5417  1.6E+05 0.01881 0.97901 0       0.00208 0.9811  
131.7   1       50      1.0195  1.3E+05 0.01888 0.97901 0       0.00074 0.97976 
159.3   1       50      0.69686 1.1E+05 0.0191  0.97901 0       0.00029 0.97931 
206.5   1       50      0.4147  85465   0.01962 0.97901 0       8.2E-05 0.9791  
260.4   1       50      0.26079 67775   0.02027 0.97901 0       2.6E-05 0.97904 
michael@michael-desktop:~/Downloads/pfcalc-1.1/src$ 

```

Good luck!

---

### Post by texpat on 2012-12-30
> **mc4man said:**
> Worst case if you can't square up source - 
Install gcc-4.4
clean your source or start fresh, configure with 

```
CC=gcc-4.4 ./configure
```

I'm afraid this is too advanced for me. I suppose I'd manage to install gcc-4.4 but I have no clue what you mean by 

> clean your source or start fresh, configure with 

```
CC=gcc-4.4 ./configure
```

If it comes to it, I'll get back to you on that one. In the mean time I may get lucky and the developer gets back to me.

---

### Post by texpat on 2012-12-30
@MG&TL:

Cheers mate! You got it running for me. I can't believe

a) you went to all the trouble of downloading and fixing someone else's code/scripts, and

b) the speed in which you did this.

Thanks again and Season's Greetings to all who contributed to this thread.

---

