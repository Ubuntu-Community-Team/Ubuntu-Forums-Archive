---
title: "Tried to restore xorg.conf, now I have an error!"
date: 2008-01-21
forum: General Help
---

### Post by Full-choke on 2008-01-21
When I turn the computer on I get a very patriotic screen saying the following, "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"  If I click "Yes" I get the following:

X Window System Version 7.2.o
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2 
Build Operating System: Linux Ubuntu
Current Operating System: Linux ice 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686
Build Date: 18 Dec 2008
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version.
Module Loader present
Markers (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 21 11:43:37 2008
(==) Using config file: "/etc/X11/xorg.conf"

I get that exact screen twice

I then get a little screen that says, "The x server is now disabled.  Restart the GDM when it is configured correctly."

Under my /etc/X11 I have the following:

app-defaults
cursors
default-display-manager
fonts
gdm
rgb.txt
X
xinit

xkb
xorg.conf
xorg.conf~
xorg.conf.backup
xorg.conf.fglrk-0
xorg.conf.good (this is my backup of the backup)
xorg.conf.original-0
Xresources

xserver
xsession
xsession.d
xsession.options
XvMCConfig
Xwrapper.config

Is everything that's supposed to be there in there?  Or is there too much, it seems like a lot of different xorg.conf stuff then the last time I was in there.  Any help would be wonderful, thanks...

F-C

---

### Post by stump138 on 2008-01-21
since you have a backup have you tried:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
?

If you can do that and restart x by trying 
```
startx
```
You should be up and going again.

If you can't get it going at all you can try
```
sudo dpkg-reconfigure xserver-xorg
```
and that will allow you to create a new xorg.conf file
gl!

---

### Post by Full-choke on 2008-01-21
Ok, it got an error on "startx"...so I went on to the reconfigure.  But I'm gonna need some help as to what to do in there, I've never done something like that before.

Thanks,
F-C

---

### Post by gangrelsurf on 2008-01-21
A few questions - 
What kind of graphics card are you using?
```
lspci
```
what driver are you using? The nvidia restricted, I suspect.
```
cat /etc/X11/xorg.conf | grep Driver
```
Did you recently update the kernel?

Could you post the output of this:
```
cat /var/log/Xorg.0.log | grep EE
```
That will output all the lines from your xorg log that indicate errors

---

### Post by az on 2008-01-21
> **Full-choke said:**
> Ok, it got an error on "startx"...so I went on to the reconfigure.  But I'm gonna need some help as to what to do in there, I've never done something like that before.

Thanks,
F-C

Did it ever work?

If that'S the case, then boot into recovery mode.  This dosn't use X, so your hardware can be properly probled.  Some hardware cannot be probed when in use (even if it's not working)

Once at the command-line run

dpkg-reconfigure -phigh xserver-xorg

That should reconfigure the X server without asking you any questions.  It will also make a backup of your previous xorg.conf file (timestamped) so there is no need to copy the file beforehand yourself.

Them go into graphics mode by running:

init 2

That should have reconfigured your graphics to the way they were when you first installed.

---

### Post by Full-choke on 2008-01-21
What kind of graphics card are you using?
VGA Compatible Controller: Intel Corporation 82945G/G2 Internal Graphics Controller

What driver are you using? The nvidia restricted, I suspect.
The answers:
"kbd"
"mouse"
"wacom"
"wacom"
"wacom"
"i810"

Could you post the output of this:
    (WW) warning, (EE) error, (NI) Not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "i810" (module does not exist, 0)
(EE) No drivers available

My dad and I tried a few different drivers the other day but nothing worked.  I tried another this morning and I have been in trouble ever since...

F-C

---

### Post by gangrelsurf on 2008-01-21
Ok, so you are using the i810 drivers but they aren't there. 
My guess that you had updated the kernel and the nvidia drivers didn't match your new kernel version was dead wrong. Did you try what az said?

If you try that and still get errors, try this:
modprobe i810
<what az says, including the 'init 2'>

if that works, try a reboot

---

### Post by Full-choke on 2008-01-21
Okay, ran what Az posted and I'm back up and running.  But, the highest resolution I can run is 1024x768...is there a way I can get that higher like I used to?

Thanks so much for all your help guys, at least I have a good computer again now and I can get off this cursed M$ machine, lol.

F-C

---

