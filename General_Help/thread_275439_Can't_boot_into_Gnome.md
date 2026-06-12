---
title: "Can't boot into Gnome?"
date: 2006-10-11
forum: General Help
---

### Post by sega on 2006-10-11
I have a dedicated server running that has Ubuntu Server installed on it. I changed the sources.list so it looked like this 
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

(My old sources.list had artfiles.org instead of ubuntu.com and i did run it once before editing it)

I ran 
sudo apt-get update
sudo apt-get install ubuntu-desktop

Everything seem to be ok so far.

I ran 
sudo dpkg-reconfigure xserver-xorg
But i'm not sure if I needed to do that but I don't think I changed anything.

Then from the command line I ran
startx

When I do I get this error

xauth:  creating new authority file /root/.serverauth.30770

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

What could be the problem?
I running WindowsXP with PuTTY to SSH into the server

---

### Post by aysiu on 2006-10-11
Have you tried removing /tmp/.X0-lock?

---

### Post by taurus on 2006-10-11
Looks like you already have GUI login screen running!  See what happens when you press <Ctrl><Atl>F7.  It would "kick" you back to the GUI login screen.  Otherwise, reboot and that should be it...

---

### Post by sega on 2006-10-11
When I press <Ctrl><Atl>F7 it just displays this ^[^[[18~
Even when I reboot the server it doesn't start up Gnome it just goes to the command line. Could this be something to with PuTTY?
Like it's not showing the GUI/Gnome with PuTTY.

How do I remove /tmp/.X0-lock?

---

### Post by aysiu on 2006-10-11
```
sudo rm /tmp/.X0-lock
``` should work.

---

### Post by sega on 2006-10-11
> **aysiu said:**
> ```
sudo rm /tmp/.X0-lock
``` should work.

Ok I tried that but I get this error now.

```

root@reverse:~# sudo rm /tmp/.X0-lock
root@reverse:~# startx
xauth:  creating new authority file /root/.serverauth.30846

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux reverse 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  6 07:05:25 2004
(==) Using config file: "/etc/X11/xorg.conf"
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
error opening security policy file /etc/X11/xserver/SecurityPolicy
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

```

What could be the problem there?

---

### Post by aysiu on 2006-10-11
It's not looking good...

I did [a Google search for your error](http://www.google.com/search?num=100&hl=en&lr=&safe=off&q=startx+X%3A+warning%3B+process+set+to+priority+-1+instead+of+requested+priority+0&btnG=Search), and there were only three results--none had solutions.

---

### Post by sega on 2006-10-11
Do you think uninstalling Gnome and reinstalling it will work?

---

