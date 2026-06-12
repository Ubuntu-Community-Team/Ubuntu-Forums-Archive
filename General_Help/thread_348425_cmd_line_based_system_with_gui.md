---
title: "cmd line based system with gui"
date: 2007-01-28
forum: General Help
---

### Post by Darth_tater on 2007-01-28
im going to be reinstalling ubuntu 6.06 LTS (i should have made backups :( )

i will use the box primarily as web server but i will also need a light weight GUI for emergencies (when i dont have any other computer to use *but* this box)

my question is this:

1) how can i install 6.06 LTS so that it will boot only the services/daemons needed for acting as a server, but if need be, i can start X server and some window manager (something light weight)

2) i dont need 1/2 the services that ubuntu installs for the desktop environment (the HP printer daemon, ESD sound manager, ect...)  so how can i customize exactly what services are starting up for the GUI environment?

3) is there a update manager, similar to the one in Gnome, that will work from the CLI  (as in, it boots up with the computer, but lets (a few selected users) know if there are any updates as soon as they log in from the CLI)

thanks soo much (in advance) for your help!

---

### Post by phersotty on 2007-01-28
I don't know the answer to your question, but it is interesting that Ubuntu doesn't ask what packages to include during installation like other many distros do.  Maybe this would be a good feature request though.  Although I haven't tried it, maybe the text installer offers more options.

---

### Post by meng on 2007-01-28
> **phersotty said:**
> I don't know the answer to your question, but it is interesting that Ubuntu doesn't ask what packages to include during installation like other many distros do.  Maybe this would be a good feature request though.  Although I haven't tried it, maybe the text installer offers more options.
I assume this is to "simplify" things for the end-user by not confusing them with too many choices (go figure). Anyhow, the OP's problem can be addressed by installing the Server Edition, then installing a window manager or desktop environment of choice on top of that, perhaps icewm or fluxbox.

Not sure about perusing updates from CLI, perhaps:
sudo apt-get upgrade -s
(simulates)

---

### Post by aysiu on 2007-01-28
You can do this: ```
sudo apt-get update
sudo apt-get install x-window-system-core icewm update-notifier
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Darth_tater on 2007-01-28
> **meng said:**
> I assume this is to "simplify" things for the end-user by not confusing them with too many choices (go figure). Anyhow, the OP's problem can be addressed by installing the Server Edition, then installing a window manager or desktop environment of choice on top of that, perhaps icewm or fluxbox.

Not sure about perusing updates from CLI, perhaps:
sudo apt-get upgrade -s
(simulates)

yes.. i think ubuntu is great for people that like simple things.  however, i wish that there would be a Yast (suse) like installer for ubuntu as well for people that want to customise their ubuntu distros.  

the reason why i *dont* use suse is that Ubuntu (i've found through experiance) has much better hardware support when compared to suse.  and, ubuntu juut works (tm) where suse requires configuration 

i would normally do this, however i need apache 2 support and the server installation disk does not ship with apache 2 support.  

ill take a look at the alternate install disk and see if it offers me a cmd line based solution.

---

### Post by Darth_tater on 2007-01-28
> **aysiu said:**
> You can do this: ```
sudo apt-get update
sudo apt-get install x-window-system-core icewm update-notifier
sudo dpkg-reconfigure xserver-xorg
startx
```

would this be ontop of the server installation or just the cmd line installation ?

i dont think it matters, but id like to know before i commit my torrent client for a few days (i have a small pipe)

---

### Post by aysiu on 2007-01-28
It would work for either a server installation off the Server CD or the "install a server" option off the Alternate CD.

---

### Post by Darth_tater on 2007-01-29
> **aysiu said:**
> It would work for either a server installation off the Server CD or the "install a server" option off the Alternate CD.

only problem, i need apache 2 support and afaik, the server installation does not have apache 2 (its got 1.X i think...)

ill try installing a cmd line only system, then installing apache 2 and a light weight GUI.



thanks for all your help!

---

### Post by Darth_tater on 2007-01-29
```
Darth@MultiServ:~$ sudo apt-get install x-window-system-core icewm update-notifier
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package x-window-system-core is a virtual package provided by:
  xorg 1:7.1.1ubuntu6.2
You should explicitly select one to install.
E: Package x-window-system-core has no installation candidate
```

when i try to specifically install " xorg 1:7.1.1ubuntu6.2" i get an error.
 whats the actual command i need to enable for this to work ?

edit: whoops.. i just enabled a few more repos and re updated... its all good now!

---

### Post by aysiu on 2007-01-29
Hm. [Apparently, as of Edgy Eft](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=x-window-system-core&searchon=name&subword=1&version=all&release=all), *x-window-system-core* is now in the Universe repositories and is just a "transitional" package. I'm not sure what the new package is called...

---

### Post by Darth_tater on 2007-01-29
> **aysiu said:**
> Hm. [Apparently, as of Edgy Eft](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=x-window-system-core&searchon=name&subword=1&version=all&release=all), *x-window-system-core* is now in the Universe repositories and is just a "transitional" package. I'm not sure what the new package is called...

yep.. i enabled  the Univ. repos and its all good... 
i should have refreshed before posting! :(

---

### Post by Darth_tater on 2007-01-29
what did i do?
here is the output from "sudo startx"

```
karl@MultiServ:~$ sudo startx
Password:
xauth:  creating new authority file /home/karl/.serverauth.3606
xauth:  error in locking authority file /home/karl/.Xauthority
xauth:  error in locking authority file /home/karl/.Xauthority
xauth:  error in locking authority file /home/karl/.Xauthority
xauth:  error in locking authority file /home/karl/.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux MultiServ 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 29 11:00:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) AIGLX: Screen 0 is not DRI capable
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/libfb.so(fbOddTile+0x118) [0xb7ad2898]
3: /usr/lib/xorg/modules/libfb.so(fbTile+0x8c) [0xb7ad295c]
4: /usr/lib/xorg/modules/libfb.so(fbFillRegionTiled+0x19e) [0xb7ad320e]
5: /usr/lib/xorg/modules/libfb.so(fbPaintWindow+0x109) [0xb7ad3479]
6: /usr/bin/X11/X [0x8158a4e]
7: /usr/bin/X11/X [0x8154201]
8: /usr/bin/X11/X(compPaintWindowBackground+0x6d) [0x8191b7d]
9: /usr/bin/X11/X(miWindowExposures+0xfa) [0x8109eda]
10: /usr/bin/X11/X(MapWindow+0x332) [0x8072dc2]
11: /usr/bin/X11/X(InitRootWindow+0xbe) [0x8072f5e]
12: /usr/bin/X11/X(main+0x42f) [0x806e6bf]
13: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d298cc]
14: /usr/bin/X11/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
xauth:  error in locking authority file /home/karl/.Xauthority

```

im not sure what video driver to use (this motherboard is from an old emachines w/ integrated intel graphics) so i chose vesa driver

please help!!!

---

### Post by aysiu on 2007-01-29
I don't know what to do to fix that, but it's actually supposed to be just plain old ```
startx
``` instead of ```
sudo startx
``` One of [these threads](http://www.google.com/search?num=100&hl=en&safe=off&q=xauth%3A++error+in+locking+authority+file+.Xauthority+site%3Aubuntuforums.org&btnG=Search) should help.

---

### Post by Darth_tater on 2007-01-29
> **aysiu said:**
> I don't know what to do to fix that, but it's actually supposed to be just plain old ```
startx
``` instead of ```
sudo startx
``` One of [these threads](http://www.google.com/search?num=100&hl=en&safe=off&q=xauth%3A++error+in+locking+authority+file+.Xauthority+site%3Aubuntuforums.org&btnG=Search) should help.

i know... but sometimes sudo + command makes problems go away ;)

---

### Post by Darth_tater on 2007-01-29
im going to reinstall.

but, i did some research, i have a Socket 370, Intel 810 chipset.  should i just use the vesa driver, or is there a specific driver that i *should* install/load


thanks for your time!

edit: looks like i dont have to!!!!

somehow, the i810 graphics driver got installed (dont ask me how)  the package that i needed to install was "xserver-xorg-video-intel"
but i didnt install it.  neways... it works!!!!

---

### Post by yigal.weinstein on 2007-01-29
Darth_tater,

sudo startx starts you as root in a gui.  This is not a good idea in general. why don't you try [www.nubuntu.org/](www.nubuntu.org/) .  This seems to be exactly what you want.

---

### Post by koenn on 2007-01-29
> **aysiu said:**
> Hm. [Apparently, as of Edgy Eft](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=x-window-system-core&searchon=name&subword=1&version=all&release=all), *x-window-system-core* is now in the Universe repositories and is just a "transitional" package. I'm not sure what the new package is called...

xorg, apparently
[http://packages.ubuntu.com/edgy/x11/x-window-system-core](http://packages.ubuntu.com/edgy/x11/x-window-system-core)

---

