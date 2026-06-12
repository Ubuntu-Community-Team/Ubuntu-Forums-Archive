---
title: "Compiling GnuCash-2.0.5 from sources on Dapper"
date: 2007-03-18
forum: General Help
---

### Post by MAZDA on 2007-03-18
Hello !

I have started to build GnuCash 2.0.5 on Ubuntu Dapper from sources.

For some reason the configuration Script of GnuCash stop the build process with the following error message.

> 
checking for (g-wrap) guile module... yes
checking for (g-wrap gw-glib-spec) guile module... yes
checking for SLIB support... configure: error:

   [B]Cannot find SLIB.  Are you sure you have it installed?
   See [http://bugzilla.gnome.org/show_bug.cgi?id=347922](http://bugzilla.gnome.org/show_bug.cgi?id=347922)[/B]




Can somebody tell me what i have to do for resolving the above problem.

The Solution described in the Link above dont work in Dapper
> This wasn't enough info to point out what's wrong, so
I added some print lines to the configure file right before this error and
found:
checking for SLIB support... start DEBUG
checking for SLIB support... LD_LIBRARY_PATH= /usr/local/lib:
GUILE_LOAD_PATH= /usr/local/share/guile/site:
/usr/bin/guile -c (use-modules (ice-9 slib)) (require 'printf)
end DEBUG
configure: error:

   [B]Cannot find SLIB.  Are you sure you have it installed?
   See [http://bugzilla.gnome.org/show_bug.cgi?id=347922](http://bugzilla.gnome.org/show_bug.cgi?id=347922)[/B]

If I run the standalone guile command, I get:
ERROR: Value out of range 0 to 16: -1

Apparently, guile doesn't like the trailing ":" on GUILE_LOAD_PATH.

GUILE_LOAD_PATH is read, but not set in the configure script!
If I run 
% guile -c '(display %load-path)' (/usr/local/share/guile/site
/usr/share/guile/site /usr/share/guile/1.8 /usr/share/guile
/usr/share/guile/site /usr/share/guile/1.8 /usr/share/guile)
and then
% setenv GUILE_LOAD_PATH
/usr/local/share/guile/site:/usr/share/guile/site:/usr/share/guile/1.8:/usr/share/guile

then configure works!

I think what I did to get this to compile is beyond what any end-user is
willing to do to get this package to compile.
Please fix the configure script so that GUILE_LOAD_PATH gets set if it is not
already set.

Thanks for the help.
Greetings MAZDA

---

### Post by Lucas2005 on 2007-03-24
i'm having the exact same error on ubuntu 6.06  :( 

I followed this and all the readme files....

[http://www.linuxmint.com/forum/viewtopic.php?t=1283]("http://www.linuxmint.com/forum/viewtopic.php?t=1283")

Help would be greatly appreciated  :)

---

