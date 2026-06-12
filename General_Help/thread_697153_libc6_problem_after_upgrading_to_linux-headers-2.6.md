---
title: "libc6 problem after upgrading to linux-headers-2.6.22-14.52"
date: 2008-02-14
forum: General Help
---

### Post by chaosrl on 2008-02-14
Hi everyone,

Earlier I posted a problem with gnumeric, but I've decided to make a new thread, as I've begun to realize that my problem was not in gnumeric at all. It seems that in the latest update of linux-headers, my libc6 has been somehow broken. As I said in my other thread, gnumeric and OO Spreadsheet both crash on Save-as, and now I've discovered that gedit and evince do as well. It appears that gedit is alright with saving, must not save-as-ing (if I use "sudo gedit" and save, it will crash, but if I use "sudo gedit ~/Desktop/newfile" and save, it won't crash). evince also crashed upon a request to print. I haven't tested all of these situations extensively, but that's what I have so far.

Anyways, this is quite an inconvenience. Ubuntu is fantastic; I can't give it up now, so I'll bear with these things (along with broken suspend, I'm one of the lucky ATi users who hasn't gotten suspend to work yet), but I'd love for this to get fixed.

Here's what was upgraded last:
```

Commit Log for Tue Feb  5 00:30:58 2008


Upgraded the following packages:
linux-headers-2.6.22-14 (2.6.22-14.47) to 2.6.22-14.51
linux-headers-2.6.22-14-generic (2.6.22-14.47) to 2.6.22-14.51
linux-image-2.6.22-14-generic (2.6.22-14.47) to 2.6.22-14.51
linux-libc-dev (2.6.22-14.47) to 2.6.22-14.51
linux-source-2.6.22 (2.6.22-14.47) to 2.6.22-14.51
```

One of my friends tried to find out a little more of what was wrong, and got this:

```
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(gdb) core-file core 
Reading symbols from /usr/lib/libspreadsheet-1.7.11.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libspreadsheet-1.7.11.so
Reading symbols from /lib/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/libc.so.6
Reading symbols from /usr/lib/libgoffice-0.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgoffice-0.so.4
Reading symbols from /usr/lib/libgnomeui-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnomeui-2.so.0
Reading symbols from /usr/lib/libbonoboui-2.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libbonoboui-2.so.0
Reading symbols from /usr/lib/libgtk-x11-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgtk-x11-2.0.so.0
Reading symbols from /usr/lib/libgdk-x11-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk-x11-2.0.so.0
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libgnome-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnome-2.so.0
Reading symbols from /usr/lib/libbonobo-2.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libbonobo-2.so.0
Reading symbols from /usr/lib/libgnomevfs-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnomevfs-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgnomeprint-2-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnomeprint-2-2.so.0
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libglade-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglade-2.0.so.0
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libgnomecanvas-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnomecanvas-2.so.0
Reading symbols from /usr/lib/libart_lgpl_2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libart_lgpl_2.so.2
Reading symbols from /usr/lib/libatk-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libatk-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXi.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXi.so.6
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libXcomposite.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXfixes.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /lib/libpopt.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libpopt.so.0
Reading symbols from /usr/lib/libgsf-gnome-1.so.114...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-gnome-1.so.114
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libbonobo-activation.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libbonobo-activation.so.4
Reading symbols from /usr/lib/libgconf-2.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /lib/libdl.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/libdl.so.2
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /lib/librt.so.1...
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)...done.
Loaded symbols for /lib/librt.so.1
Reading symbols from /lib/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/libm.so.6
Reading symbols from /lib/libpthread.so.0...
(no debugging symbols found)...done.
Loaded symbols for /lib/libpthread.so.0
Reading symbols from /lib/ld-linux-x86-64.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /usr/lib/libgnome-keyring.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnome-keyring.so.0
Reading symbols from /usr/lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpcre.so.3
Reading symbols from /usr/lib/libjpeg.so.62...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/libesd.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libesd.so.0
Reading symbols from /usr/lib/libaudiofile.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libaudiofile.so.0
Reading symbols from /usr/lib/libORBitCosNaming-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBitCosNaming-2.so.0
Reading symbols from /usr/lib/libdbus-glib-1.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /usr/lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/libgnutls.so.13...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnutls.so.13
Reading symbols from /usr/lib/libavahi-glib.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libavahi-glib.so.1
Reading symbols from /usr/lib/libavahi-common.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libavahi-common.so.3
Reading symbols from /usr/lib/libavahi-client.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libavahi-client.so.3
Reading symbols from /lib/libresolv.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/libresolv.so.2
Reading symbols from /lib/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /lib/libutil.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libutil.so.1
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgailutil.so.18...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgailutil.so.18
Reading symbols from /usr/lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libXdmcp.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/libasound.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libasound.so.2
Reading symbols from /lib/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libnsl.so.1
Reading symbols from /usr/lib/libtasn1.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtasn1.so.3
Reading symbols from /usr/lib/libgpg-error.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgpg-error.so.0
Reading symbols from /usr/lib/libgcrypt.so.11...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgcrypt.so.11
Reading symbols from /lib/libsepol.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libsepol.so.1
Reading symbols from /lib/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/libnss_compat.so.2
Reading symbols from /lib/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libnss_nis.so.2
Reading symbols from /lib/libnss_files.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/libnss_files.so.2
Reading symbols from /usr/lib/gconv/ISO8859-1.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gconv/ISO8859-1.so
Reading symbols from /usr/lib/pango/1.6.0/modules/pango-basic-fc.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
Reading symbols from /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
Reading symbols from /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
Reading symbols from /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so
Reading symbols from /usr/lib/gnome-vfs-2.0/modules/libfile.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gnome-vfs-2.0/modules/libfile.so
Reading symbols from /lib/libattr.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libattr.so.1
Reading symbols from /lib/libacl.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libacl.so.1
Reading symbols from /usr/lib/libfam.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfam.so.0
Reading symbols from /usr/lib/libtrackerclient.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtrackerclient.so.0
Core was generated by `gnumeric'.
---Type <return> to continue, or q <return> to quit---
Program terminated with signal 11, Segmentation fault.
#0  0x00002aef2edc68d0 in strchr () from /lib/libc.so.6
(gdb) quit

```

At the bottom of that mess, he said that something was wrong with /lib/libc.so.6, which AFAIK is part of the libc6 package, which I can't seem to reinstall. Is there anyway to fix this, either by repair libc6 or by rolling back the linux-headers upgrade? Thanks!

---

### Post by dcstar on 2008-02-14
> **chaosrl said:**
> 
..............
At the bottom of that mess, he said that something was wrong with /lib/libc.so.6, which AFAIK is part of the libc6 package, which I can't seem to reinstall. Is there anyway to fix this, either by repair libc6 or by rolling back the linux-headers upgrade? Thanks!

Just because something was reported as the library being used when a crash occurred does not mean it is the cause of the crash.

The latest version I have installed is 2.6.22-14.52, I suggest you install those.

---

### Post by chaosrl on 2008-02-15
Hmm, alright. I'm still pretty new at all of this, so bear with me. I just noticed that my history log is showing the upgrade to *.51 for all of the kernel upgrades; however, I'm quite positive that when I checked Synaptic, my version installed was *.52. When I get back on my computer, I'll check again and see if my History has anything more recent.

---

### Post by chaosrl on 2008-02-18
Alright, I've just checked. There is no history for installing 2.6.22-14.52, just for *.51. I may have used terminal to update that (sometimes I do that :\). I do have *.52 installed. So, I have a few questions:

1) Is there any way to downgrade the 2.6.22 kernel back to *.47?
2) If not, when would the next kernel upgrade be available?, and finally
3) I have 2.6.20 and 2.6.24 installed; however, when I boot with them, my whole computer is EXTREMELY slow. Should it be doing that? Or should I be able to run those kernels smoothly?

Again, TIA for replies!

---

