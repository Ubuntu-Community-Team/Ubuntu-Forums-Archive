---
title: "Slashexec edgy gaim 2.0"
date: 2007-03-27
forum: General Help
---

### Post by Scotty562 on 2007-03-27
I want to install slashexec. All I could find was a 64 bit .rpm which helped me very little... Could someone help me get this installed?

---

### Post by paparucino on 2007-03-28
> **Scotty562 said:**
> I want to install slashexec. All I could find was a 64 bit .rpm which helped my little... Could someone help me get this installed?

try to convert your rpm  to deb with alien

---

### Post by Scotty562 on 2007-03-28
sudo alien gaim-slashexec-1.0-0.fc3.x86_64.rpm 
Password:
mkdir: cannot create directory `gaim-slashexec-1.0': File exists
mkdir: cannot create directory `gaim-slashexec-1.0/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/gaim-slashexec
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libreadline.so.4
dpkg-shlibdeps: warning: unable to find dependency information for shared library libreadline (soname 4, path libreadline.so.4, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libtermcap.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libtermcap (soname 2, path libtermcap.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libc.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: gaim-slashexec-1.0: No such file or directory

---

### Post by paparucino on 2007-03-28
> **Scotty562 said:**
> sudo alien gaim-slashexec-1.0-0.fc3.x86_64.rpm 
Password:

find: gaim-slashexec-1.0: No such file or directory

I've found this thread. Look for post nbr 15 by mshima. There is a deb for you.
I hope :-)

---

### Post by Scotty562 on 2007-03-28
> **paparucino said:**
> I've found this thread.

Which  thread :)?

I've also found this site which seems to have the slashexec has a plugin.

[http://gaim.guifications.org/trac/wiki/PluginPack#Faq1](http://gaim.guifications.org/trac/wiki/PluginPack#Faq1)

It's throwing fits installing as well.

./configure worked but when I run make it spits this out near the very end:

Making all in mystatusbox
make[2]: Entering directory `/home/aries/Desktop/gaim-plugin_pack-1.0beta6/mystatusbox'
if /bin/bash ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\" -DDATADIR=\"/usr/share\" -DLOCALEDIR=\"/usr/share/locale\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -g -O2 -Wall -g3 -MT mystatusbox.lo -MD -MP -MF ".deps/mystatusbox.Tpo" \
          -c -o mystatusbox.lo `test -f 'mystatusbox.c' || echo './'`mystatusbox.c; \
        then mv -f ".deps/mystatusbox.Tpo" ".deps/mystatusbox.Plo"; \
        else rm -f ".deps/mystatusbox.Tpo"; exit 1; \
        fi
mystatusbox.c: In function 'detach_per_account_boxes':
mystatusbox.c:132: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:134: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:136: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:136: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:136: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:149: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:149: error: request for member 'parent' in something not a structure or union
mystatusbox.c:149: warning: passing argument 2 of 'gtk_box_pack_start' from incompatible pointer type
mystatusbox.c:151: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:151: warning: passing argument 2 of 'gtk_box_pack_start' from incompatible pointer type
mystatusbox.c:157: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:157: warning: passing argument 1 of 'gtk_widget_hide' from incompatible pointer type
mystatusbox.c: In function 'attach_per_account_boxes':
mystatusbox.c:178: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:178: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:178: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:201: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:201: error: request for member 'parent' in something not a structure or union
mystatusbox.c:201: warning: passing argument 2 of 'gtk_box_pack_start' from incompatible pointer type
mystatusbox.c:202: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:202: error: request for member 'parent' in something not a structure or union
mystatusbox.c:206: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:206: warning: passing argument 2 of 'gtk_box_pack_start' from incompatible pointer type
mystatusbox.c:207: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:231: error: 'GaimGtkBuddyList' has no member named 'headline_hbox'
mystatusbox.c:231: warning: passing argument 1 of 'gtk_widget_hide' from incompatible pointer type
mystatusbox.c: In function 'gaim_gtk_status_selectors_show':
mystatusbox.c:338: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:338: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:338: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:339: error: 'GaimGtkBuddyList' has no member named 'scrollbook'
mystatusbox.c:339: warning: passing argument 1 of 'gtk_widget_size_request' from incompatible pointer type
make[2]: *** [mystatusbox.lo] Error 1
make[2]: Leaving directory `/home/aries/Desktop/gaim-plugin_pack-1.0beta6/mystatusbox'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aries/Desktop/gaim-plugin_pack-1.0beta6'
make: *** [all] Error 2

mystatusbox just gums up the entire works.

---

### Post by paparucino on 2007-03-28
> **Scotty562 said:**
> Which  thread :)?

I've also found this site which seems to have the slashexec has a plugin.

[http://gaim.guifications.org/trac/wiki/PluginPack#Faq1](http://gaim.guifications.org/trac/wiki/PluginPack#Faq1)

It's throwing fits installing as well.

ooooooooooooopppppppppsssssssssssss..... :D

[http://ubuntuforums.org/showthread.php?t=152457&page=2&highlight=gaim2](http://ubuntuforums.org/showthread.php?t=152457&page=2&highlight=gaim2)

---

### Post by Scotty562 on 2007-03-28
> **paparucino said:**
> ooooooooooooopppppppppsssssssssssss..... :D

[http://ubuntuforums.org/showthread.php?t=152457&page=2&highlight=gaim2](http://ubuntuforums.org/showthread.php?t=152457&page=2&highlight=gaim2)

That did the trick! Thanks!!

---

