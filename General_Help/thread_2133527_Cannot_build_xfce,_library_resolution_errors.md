---
title: "Cannot build xfce, library resolution errors"
date: 2013-04-08
forum: General Help
---

### Post by hwttdz on 2013-04-08
I'm having trouble building a number of different xfce packages, I assume the solution will be similar for all the packages so I will share just one at the moment.  And it seems that libgtk and libgdk are being passed to the call to libtool.  Any ideas?

When building xfwm4-4.10.0 from the 4.10 release I get the following:
```
make  all-recursive
make[1]: Entering directory `/home/user/temp/xfce/src/xfwm4-4.10.0'
Making all in defaults
make[2]: Entering directory `/home/user/temp/xfce/src/xfwm4-4.10.0/defaults'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/temp/xfce/src/xfwm4-4.10.0/defaults'
Making all in helper-dialog
make[2]: Entering directory `/home/user/temp/xfce/src/xfwm4-4.10.0/helper-dialog'
  CC     helper_dialog-helper-dialog.o
  CCLD   helper-dialog
/usr/bin/ld.bfd.real: helper_dialog-helper-dialog.o: undefined reference to symbol 'gdk_error_trap_pop'
/usr/bin/ld.bfd.real: note: 'gdk_error_trap_pop' is defined in DSO /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0 so try adding it to the linker command line
/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make[2]: *** [helper-dialog] Error 1
make[2]: Leaving directory `/home/user/temp/xfce/src/xfwm4-4.10.0/helper-dialog'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/temp/xfce/src/xfwm4-4.10.0'
make: *** [all] Error 2

```

---

### Post by Toz on 2013-04-08
Are you building this on 12.10?

I've successfullly built Xfce from git a number of times on 12.10. I followed the build instructions here: [http://docs.xfce.org/xfce/building]("http://docs.xfce.org/xfce/building"). Can you confirm that you have all of the dependencies installed? There is also a suggested order for buidling (see the linked document). 

In addition, I ran into a few gotchas building Xfce - I'll see if I can find my notes. They involved thunar and exo libraries. 

Out of curiosity, any reason why you aren't just installing the packages from a PPA as opposed to buidling from source? It is much, much easier. Saves on coffee and sleep :)

---

### Post by hwttdz on 2013-04-08
This is on 13.04 (though ubuntu seems to have changed exactly how betas work recently).

I believe I have all deps installed, but in any case I feel comfortable enough in installing dependencies.

I was helping test some new features for xfdesktop, but after upgrading to 13.04 I've had trouble building it.  The author was unable to reproduce my issues with xfdesktop build, so I decided I'd take a look at some of the other xfce packages, and found that there are more issues.  I'm debating re-installing 13.04 since the author had no issues with the same, but between having different partitions for /usr, /home and /var as well as having a fair number of modified packages it would take me a little effort to get rolling again if I go that route (even with good backups).

---

### Post by Toz on 2013-04-08
I don't currently have a spare 13.04 install to test an Xfce 4.10 build. If time permits, I'll throw a VM together and give it a go.

EDIT: Threw together a 13.04 VM, grabbed the latest Xfce source from git and have started building. Haven't run into any errors yet (still need to build some apps and plugins). Xfwm built fine.

Here is the list of dependencies that I install to build Xfce:
```
git 
build-essential 
intltool 
libtool 
libglib2.0-dev 
gtk-doc-tools 
libdbus-1-dev 
libdbus-glib-1-dev 
libextutils-depends-perl 
libextutils-pkgconfig-perl 
xserver-xorg-dev 
libgtk2.0-dev 
libstartup-notification0-dev 
libwnck-dev 
libgudev-1.0-dev 
libnotify-dev 
libexif-dev 
libpng12-dev 
libjpeg-dev 
libxklavier-dev 
libffmpegthumbnailer-dev 
libgstreamer0.10-dev 
libgsf-1-dev 
libpoppler-glib-dev 
libopenrawgnome-dev 
libindicator-dev 
libupower-glib-dev 
libsoup2.4-dev 
libgstreamer-plugins-base0.10-dev 
libburn-dev 
libisofs-dev 
libvte-dev 
libgstreamer1.0-dev 
libcurl4-gnutls-dev 
libgstreamer-plugins-base1.0-dev 
libgtksourceview2.0-dev 
libgtk-3-dev 
libcurl4-gnutls-dev 
libtag1-dev

```
...to build the following components:
```
XFCE_CORE="xfce4-dev-tools libxfce4util xfconf libxfce4ui garcon exo xfce4-panel thunar xfce4-settings xfce4-session xfwm4 xfdesktop xfce4-appfinder gtk-xfce-engine tumbler thunar-volman"

XFCE_PLUGINS="xfce4-indicator-plugin xfce4-weather-plugin xfce4-genmon-plugin xfce4-places-plugin"

XFCE_APPS="parole xfburn xfce4-terminal ristretto gigolo mousepad"

```

Perhaps you're missing a dependency?

---

### Post by Toz on 2013-04-09
Just finished rebuilding the whole thing in 13.04. There appear to be some issues with this version of ubuntu. Specifically:

1. Per-workspace background settings (see [bug 369]("https://bugzilla.xfce.org/show_bug.cgi?id=369"))
2. xfdesktop crashing on start (still need to investigate this, might be related to #1)

However, it did build successfully and I did not run into the error you are getting. I built from git not from the packages.

---

### Post by hwttdz on 2013-04-09
Yeah, that's the original bug I filed against the source package when I thought it was there.  I'll go update that now.

I reinstalled 12.10 (and there was much pulling of hair and teeth), and I'm going to hold off upgrading at the moment this time.

---

