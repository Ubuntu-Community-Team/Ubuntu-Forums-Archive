---
title: "How to run startx in rc.local?"
date: 2007-09-17
forum: General Help
---

### Post by dorice on 2007-09-17
I want to run startx in rc.local, and I have disabled gdm service, but I get the following error message:
>   1 xauth:  creating new authority file /.serverauth.4915
  2
  3 X: warning; process set to priority -1 instead of requested priority 0
  4
  5 X Window System Version 7.2.0
  6 Release Date: 22 January 2007
  7 X Protocol Version 11, Revision 0, Release 7.2
  8 Build Operating System: Linux Ubuntu
  9 Current Operating System: Linux domain-ubuntu 2.6.20-16-generic #1 SMP Thu Jun 21 09:30:14 CEST 2007 i686
 10 Build Date: 04 April 2007
 11     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
 12     to make sure that you have the latest version.
 13 Module Loader present
 14 Markers: (--) probed, (**) from config file, (==) default setting,
 15     (++) from command line, (!!) notice, (II) informational,
 16     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
 17 (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 12 14:47:08 2007
 18 (==) Using config file: "/etc/X11/xorg.conf"
 19 (WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
 20 (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
 21     No such file or directory.
 22 Error opening /dev/input/wacom : Success
 23 (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
 24     No such file or directory.
 25 Error opening /dev/input/wacom : Success
 26 (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
 27     No such file or directory.
 28 Error opening /dev/input/wacom : Success
 29 Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
 30 Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
 31 Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
 32 ^M
 33 waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
 34
 35 ^M
What is the problem?

---

### Post by jamvegan on 2007-09-17
Well...I'm not sure what all of your error messages mean, but isn't startx a user command?  And doesn't rc.local run system commands?  The only way that I've ever heard of startx being used is that a user logs in, and then runs startx.  Could that be the problem?

---

### Post by dorice on 2007-09-17
I see. But I don't want to login. I want to do some tests automatically in rc.local. However, if the test script contains startx, it would fail. I cannot call startx without login. Any configuration files can enable this?

---

### Post by kerry_s on 2007-09-17
look here> [http://ubuntuforums.org/showthread.php?p=3348011#post3348011](http://ubuntuforums.org/showthread.php?p=3348011#post3348011)

i been plumbing all day so my hands are killing me, so just let me know which part you get stuck on.

---

### Post by dorice on 2007-09-17
You mean I still need login? 
The method is too complex, because I need to do all things automatically in the first reboot after installation finish. And I want to support other distributions, including Fedora, SuSE, ...
If it indeed need login, there are many ways. But I am searching one without login.

---

### Post by kerry_s on 2007-09-17
1. someone has to own the process, so someone has to log in before you can startx

2. other distributions are started at grub, has nothing to do with starting X

3. good luck :)

---

