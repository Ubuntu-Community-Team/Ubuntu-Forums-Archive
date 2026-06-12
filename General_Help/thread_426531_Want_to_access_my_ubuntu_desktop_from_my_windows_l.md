---
title: "Want to access my ubuntu desktop from my windows laptop"
date: 2007-04-28
forum: General Help
---

### Post by jmartrican on 2007-04-28
Hello,

I think accessing my Ubuntu's desktop from my windows laptop is possible but dont know how.  I think I have done this years ago using cygwin at work, but I don't recall.  

Thanks a lot!
jose

---

### Post by ohioboy757 on 2007-04-28
It depends on the type of access you want.

Do you want a gui interface?  VNC is will allow this but does introduce security risks.
Do you want terminal access?  Run ssh server on Ubuntu and use putty or someone Windows client for access.

Let me know what type of access you want and I can provide more details.

---

### Post by jmartrican on 2007-04-28
GUI access.  I am using this in my local LAN, so not concerned with security just yet.  I will eventually want to access from work.

---

### Post by ohioboy757 on 2007-04-28
```
sudo aptitude install vnc4server
```

This will install the VNC server.

download a Windows VNC viewer.
[http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_x86_viewer.zip?download](http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_x86_viewer.zip?download)

When you are ready to use it over the Internet use Google to look for VNC over SSH.  This will provide more security.

---

### Post by jmartrican on 2007-04-28
Awesome.  I will give it a try and post back the results.  Thanks!

jose

---

### Post by jmartrican on 2007-04-28
Having problem s getting vnc to work.  Looks like I'm having X problems with openning a display.


```
root@jmart1:~/.vnc# ./xstartup
xsetroot:  unable to open display ''
root@jmart1:~/.vnc# vncconfig: unable to open display ""

(gnome-terminal:32334): Gtk-WARNING **: cannot open display:
Window manager error: Unable to open X display

root@jmart1:~/.vnc# vncserver

New 'jmart1:1 (root)' desktop is jmart1:1

Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/jmart1:1.log

root@jmart1:~/.vnc#
root@jmart1:~/.vnc#
root@jmart1:~/.vnc# cat jmart1\:1.log

Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc


Sat Apr 28 17:19:13 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from
list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from
 list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from l
ist!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from
list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from
 list!

Fatal server error:
could not open default font 'fixed'
xsetroot:  unable to open display 'jmart1:1'
vncconfig: unable to open display "jmart1:1"
Window manager error: Unable to open X display jmart1:1

(gnome-terminal:32351): Gtk-WARNING **: cannot open display:
root@jmart1:~/.vnc#
```

---

### Post by jmartrican on 2007-04-29
OK now I'm getting somewhere.  I installed xinitd and added the Xvnc service.  I got the vncviewer for windows and connected to my server.  After having password problems for 30 minutes I finally got the server to take ym password.

The problem now is that all I have is an X mouse pointer.... no desktop.  Any ideas what I got to do now?

Xvnc is using display 1:1.

---

### Post by jmartrican on 2007-04-29
I noticed some other folks had the same problem.  They were told to do the following:

[INDENT]System->Administration->Login Window
Click on Remote Tab
Changed style to "Same as Local"
Click on the "Configure XDMCP..." buton
Uncheck "Honor indirect request"
Click Close on both windows

reboot[/INDENT]

But I don't have GUI access to my server, so I need the CLI equiv.  

I think instructions should be given for CLI by default and GUI on demand....:-)

I also rebooted but to no avail.

---

### Post by jmartrican on 2007-04-29
OK its working.  I went to /etc/gdm/gdm.conf and enabled everything having to to do with XDMCP.

woohooo.

---

### Post by giranmoo2 on 2007-04-29
root@lrw155:~# startx
xauth:  creating new authority file /root/.serverauth.5419


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux lrw155.vectoral.info 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 29 23:01:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
Could not init font path element /usr/share/X11/fonts/misc/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/X11/fonts/75dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.


Can someone help me please, I can't connect at all to a vncserver.

---

### Post by jmartrican on 2007-04-29
giranmoo,

Do you have xinitd installed?

---

