---
title: "[SOLVED] fglrx seg fault"
date: 2008-07-01
forum: General Help
---

### Post by jon.mithe on 2008-07-01
Hi,

I have installed this and it all seems sortof but not quite. When run fglrxinfo or fgl_glxgears it seg faults (Segmentation fault is the only thing printed to the screen).  However, running as root (sudo fglrxinfo) and everything seems to work (including the gears demo) - here is the info:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.1.7412 Release

I have 2 screens, a widescreen and a standard screen left of it setup via aticonfig + pair mode.

Anyone know if this is functioning properly?  

uname -a = 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

I heard using an older version of the ati drivers work, but am not sure.

Any help would be great thanks,
Jon.

---

### Post by jon.mithe on 2008-07-02
All the glxgears etc all get the same "Segmentation fault" text unless I run as sudo.  This all started when I upgraded from 7.10 where everything worked fine.

any way of debugging this?

---

### Post by khristian on 2008-07-09
It's segfaulting here too, but it shows something before doing so:
```

$ export LIBGL_DEBUG=verbose
$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.50.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7659 Release

Falha de segmentação
```

I tried installing both the driver from the ubuntu repositories and the one directly from ATI's site.

I checked the wiki.cchtml guide that mentioned some file without read permission, but as shown above it doesn't seem to be the case.

Any clues?
:confused:

---

### Post by jon.mithe on 2008-07-18
Well I have solved my problem, reading the comments at the bottom of this.

[https://bugs.launchpad.net/ubuntu/+bug/224160](https://bugs.launchpad.net/ubuntu/+bug/224160)

My problem was basically on the dist upgrade ubuntu or ati left an out of date library that my user was calling (probably something in the fglrx config file / paths or something magical) but my root was using the other / correct one - which is why I experienced no problems as root.

I'm not too sure if this will help you khristian as you are getting information out but it might be worth trying the first step to see if you have the same problem. In the thread I showed you you can run this command:

```
find /usr/lib -name libGL.so.1 -exec ls -al {} \;
```

It will find all instances of those that library worth worrying about and the ls -la on the end will show you the creation date.  Basically remove the old ones leaving the newest (sudo mv them rather than deleting them just incase).  My new one was in /usr/lib and the old one causing the trouble was in /usr/lib/xorg and there might be something in /usr/lib/fglrx.  The thread I posted has more complete details, I cut and copied it here so the link doesnt die:

[QUOTE=Zdenko Rohac]
Hi.
This should work if you have same problem as I had: - segfault as normal user and no error as root:
Run following command in shell:

find /usr/lib -name libGL.so.1 -exec ls -al {} \;

It will show something like:
lrwxrwxrwx 1 root root 21 2008-05-23 10:10 /usr/lib/libGL.so.1 -> /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root 27 2008-05-02 18:23 /usr/lib/xorg/libGL.so.1 -> /usr/lib/fglrx/libGL.so.1.2
which means: I have found two files with this name under /usr/lib both are "links" pointing to
some "real" file path and filename is behind -> . Now list those "real" files:

ls -al /usr/lib/libGL.so.1.2
ls -al /usr/lib/fglrx/libGL.so.1.2

It will show that modify time of file in /usr/lib/fglrx directory is much older than that of file in /usr/lib also sizes
differs so /usr/lib is newer (hopefully also better) but running program is taking this older one first. So we need
to move it out of the way (from directories where programs look for libraries. /usr/lib is one of default locations,
/usr/lib/fglrx is usually defined in environment see env | grep LD_LIBRARY_PATH ). So you need to move files
/usr/lib/xorg/libGL.so.1 and /usr/lib/fglrx/libGL.so.1.2 somewhere else f.e. /tmp/ (you can delete them but if something
will go wrong you have problem} so run:

sudo mv /usr/lib/xorg/libGL.so.1 /tmp/
sudo mv /usr/lib/fglrx/libGL.so.1.2 /tmp/

and than it should work.

[/QUOTE]

---

