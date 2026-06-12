---
title: "Need help installing i havent a clue where to begin"
date: 2008-06-23
forum: General Help
---

### Post by Mr.Useless on 2008-06-23
I hope i can get a quick reply on this one its 3am

Ok so i just installed Ubuntu, sound works fine along with everything else.

lol..

I wanted to install XChat because i rpefer it to pidgeon, not bear in mind this is the first thing i have ever attempted with linux, ever.

I downloaded xChat and ran ./configure

says i need gtk, so i download that..

along the way on the website for Gtk to work i need, Glib, and Pango, so i download those too, goto install glib says i need some Gettext thing, so i go and download that, and finally get somwhere when i type ./configure

so it goes on for like 5 mins whizzing through a crap loadda text, and finally stops, so i type make..

yet again for another 5 mins is hammers the terminal wiht loads of unreadable text (cos of speed not like its gibberish, well to me it is...)

and at the end of that, i do make install..

and here what pops up..

```
ryan@Ryan-Linux:~/gettext-0.16.1$ make install
Making install in gnulib-local
make[1]: Entering directory `/home/ryan/gettext-0.16.1/gnulib-local'
make[2]: Entering directory `/home/ryan/gettext-0.16.1/gnulib-local'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/ryan/gettext-0.16.1/gnulib-local'
make[1]: Leaving directory `/home/ryan/gettext-0.16.1/gnulib-local'
Making install in gettext-runtime
make[1]: Entering directory `/home/ryan/gettext-0.16.1/gettext-runtime'
Making install in doc
make[2]: Entering directory `/home/ryan/gettext-0.16.1/gettext-runtime/doc'
make[3]: Entering directory `/home/ryan/gettext-0.16.1/gettext-runtime/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ryan/gettext-0.16.1/gettext-runtime/doc'
make[2]: Leaving directory `/home/ryan/gettext-0.16.1/gettext-runtime/doc'
Making install in intl
make[2]: Entering directory `/home/ryan/gettext-0.16.1/gettext-runtime/intl'
if { test "gettext-runtime" = "gettext-runtime" || test "gettext-runtime" = "gettext-tools"; } \
	   && test 'no' = yes; then \
	  /bin/mkdir -p /usr/local/lib /usr/local/include; \
	  /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
	  /bin/sh ../libtool --mode=install \
	    /usr/bin/install -c -m 644 libintl.la /usr/local/lib/libintl.la; \
	  if test "no" = yes; then \
	    dependencies=`sed -n -e 's,^dependency_libs=\(.*\),\1,p' < /usr/local/lib/libintl.la | sed -e "s,^',," -e "s,'\$,,"`; \
	    if test -n "$dependencies"; then \
	      rm -f /usr/local/lib/libintl.la; \
	    fi; \
	  fi; \
	else \
	  : ; \
	fi
if test "gettext-runtime" = "gettext-tools" \
	   && test 'no' = no \
	   && test yes != no; then \
	  /bin/mkdir -p /usr/local/lib; \
	  /bin/sh ../libtool --mode=install \
	    /usr/bin/install -c -m 644 libgnuintl.la /usr/local/lib/libgnuintl.la; \
	  rm -f /usr/local/lib/preloadable_libintl.so; \
	  /usr/bin/install -c -m 644 /usr/local/lib/libgnuintl.so /usr/local/lib/preloadable_libintl.so; \
	  /bin/sh ../libtool --mode=uninstall \
	    rm -f /usr/local/lib/libgnuintl.la; \
	else \
	  : ; \
	fi
if test 'no' = yes; then \
	  test yes != no || /bin/mkdir -p /usr/local/lib; \
	  temp=/usr/local/lib/t-charset.alias; \
	  dest=/usr/local/lib/charset.alias; \
	  if test -f /usr/local/lib/charset.alias; then \
	    orig=/usr/local/lib/charset.alias; \
	    sed -f ref-add.sed $orig > $temp; \
	    /usr/bin/install -c -m 644 $temp $dest; \
	    rm -f $temp; \
	  else \
	    if test yes = no; then \
	      orig=charset.alias; \
	      sed -f ref-add.sed $orig > $temp; \
	      /usr/bin/install -c -m 644 $temp $dest; \
	      rm -f $temp; \
	    fi; \
	  fi; \
	  /bin/mkdir -p /usr/local/share/locale; \
	  test -f /usr/local/share/locale/locale.alias \
	    && orig=/usr/local/share/locale/locale.alias \
	    || orig=./locale.alias; \
	  temp=/usr/local/share/locale/t-locale.alias; \
	  dest=/usr/local/share/locale/locale.alias; \
	  sed -f ref-add.sed $orig > $temp; \
	  /usr/bin/install -c -m 644 $temp $dest; \
	  rm -f $temp; \
	else \
	  : ; \
	fi
if test "gettext-runtime" = "gettext-tools"; then \
	  /bin/mkdir -p /usr/local/share/gettext/intl; \
	  /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
	  /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
	  dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin export.h gmo.h gettextP.h hash-string.h loadinfo.h plural-exp.h eval-plural.h localcharset.h lock.h relocatable.h xsize.h printf-args.h printf-args.c printf-parse.h wprintf-parse.h printf-parse.c vasnprintf.h vasnwprintf.h vasnprintf.c os2compat.h libgnuintl.h.in bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c hash-string.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c lock.c relocatable.c langprefs.c localename.c log.c printf.c version.c osdep.c os2compat.c intl-exports.c intl-compat.c"; \
	  for file in $dists; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  chmod a+x /usr/local/share/gettext/intl/config.charset; \
	  dists="plural.c"; \
	  for file in $dists; do \
	    if test -f $file; then dir=.; else dir=.; fi; \
	    /usr/bin/install -c -m 644 $dir/$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c libgnuintl.h libgnuintl.h_vms Makefile.vms libgnuintl.h.msvc-static libgnuintl.h.msvc-shared Makefile.msvc"; \
	  for file in $dists; do \
	    rm -f /usr/local/share/gettext/intl/$file; \
	  done; \
	else \
	  : ; \
	fi
make[2]: Leaving directory `/home/ryan/gettext-0.16.1/gettext-runtime/intl'
Making install in intl-java
make[2]: Entering directory `/home/ryan/gettext-0.16.1/gettext-runtime/intl-java'
cd . && test ! -d /usr/lib/jdk1.1.8 || env PATH=/usr/lib/jdk1.1.8/bin:$PATH javadoc -d javadoc1 gnu/gettext/*.java
cd . && test ! -d /usr/lib/jdk1.3.1 || env PATH=/usr/lib/jdk1.3.1/bin:$PATH javadoc -d javadoc2 gnu/gettext/*.java
make[3]: Entering directory `/home/ryan/gettext-0.16.1/gettext-runtime/intl-java'
make[3]: Nothing to be done for `install-exec-am'.
/bin/mkdir -p /usr/local/share/gettext
/bin/mkdir: cannot create directory `/usr/local/share/gettext': Permission denied
make[3]: *** [install-classes-no] Error 1
make[3]: Leaving directory `/home/ryan/gettext-0.16.1/gettext-runtime/intl-java'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/ryan/gettext-0.16.1/gettext-runtime/intl-java'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ryan/gettext-0.16.1/gettext-runtime'
make: *** [install-recursive] Error 1
```

all the folders are in my home directory, not sure if this is correct cant find any posts on noobs and where to begin..

and when i go to try the Glib installation again this happens (Same as before)


```
configure: error:
*** You must have either have gettext support in your C library, or use the
*** GNU gettext library. (http://www.gnu.org/software/gettext/gettext.html
```


I havent a clue on what to do all i want to do is install XChat and then get onto some other stuff...

Please Help

Ryan..   :confused::confused::confused:

---

### Post by sdennie on 2008-06-23
Try:

```

sudo apt-get install xchat

```

Then, look for xchat in Applications->Internet.  Installing software in Ubuntu rarely means compiling it.  Look in Applications->Add/Remove for more software you can install.

---

### Post by ad_267 on 2008-06-23
Do what vor said then give this a read: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by supergenius23 on 2008-06-23
I used this website when I first installed Ubuntu.. It gave me some good instructions and tips when 1st installing...

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron")

hope this helps :)

Go straight to page 4 and 5

---

### Post by molotov00 on 2008-06-23
Before Ubuntu you'd need to install all the dependencies and everything. But that was like me messing with Redhat 10 years ago. Ubuntu has come a long way (specifically Debian has, with its apt-get command). apt-get automatically downloads dependencies. But before it will find xchat (as per above instructions) you will need to update your sources.list file. This only needs to be done once, and basically tells apt-get that it's ok to look on the internet for xchat, rather than ONLY on your CD, which is the default.

Try and figure out the way these things work. It will save you time/effort later. Here's a little something about "repositories":
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Generally, once you add the right repositories in sources.list you can install and run apps very easily:

sudo apt-get install program-name
program-name #to run it... (or look in your menu)

---

### Post by Mr.Useless on 2008-06-23
Thanks a guys, you just made my....morning

I will look through those posts, very quick, can i +rep u or summin?

Thanks

---

### Post by molotov00 on 2008-06-23
There's a "medal" icon in the bottom right of all of our posts. Clicking that is a "thanks" and is reflected under our names. "Thanked x times in x posts"

Glad we could help.

---

### Post by mandarke on 2009-01-09
> **sdennie said:**
> Try:

```

sudo apt-get install xchat

```

Then, look for xchat in Applications->Internet.  Installing software in Ubuntu rarely means compiling it.  Look in Applications->Add/Remove for more software you can install.

what if you want to install from source?

---

