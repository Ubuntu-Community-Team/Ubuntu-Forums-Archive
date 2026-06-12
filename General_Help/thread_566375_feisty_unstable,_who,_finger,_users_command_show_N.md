---
title: "feisty unstable, who, finger, users command show NO one logged in"
date: 2007-10-03
forum: General Help
---

### Post by cltrujil on 2007-10-03
Hi everybody, I hope you can help me, since a couple of weeks my feisty is unstable, the first thing is that all the commands that should show the users logged in the machine, show NO users logged, for example:
root@pc:~# who
root@pc:~# w
 12:11:22 up 19 min,  0 users,  load average: 0,24, 0,22, 0,18
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
root@pc:~# users
root@pc:~# finger
No one logged on.

Well the last command show me right information, because it shows me the following:
claudio  pts/1        :0.0             Wed Oct  3 12:13   still logged in   
claudio  pts/0        :0.0             Wed Oct  3 11:53   still logged in   
claudio  :0                            Wed Oct  3 11:52   still logged in   
reboot   system boot  2.6.20-16-generi Wed Oct  3 11:52 - 12:13  (00:20)    
claudio  pts/0        :0.0             Wed Oct  3 11:49 - 11:51  (00:01)
I think this is right because I have 2 terminals still open. Well this is the first, and now I have problems to start the gdm, It chashed, I saw the /var/log/gdm/ and the last file modified tells me the following:

Current Operating System: Linux pc 2.6.20-16-generic #2 SMP Sun Sep 23 19:50
:39 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  3 11:52:23 2007
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from li
st!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from l
ist!
ProcXCloseDevice to close or not ?

Well the only things that could affect the system that I did, it were to change the screen that is shown at startup, I returned to the normal ubuntu screen, and I also changed the login screen and I'm using other theme in gnome. Well I don't understand what is happening but the system is clearly unstable, also I can hibernate, but sometimes it works sometimes don't. Well I have an Dell XPSM1210, and I am looking for help because I really like ubuntu in general and I haven't had this kind of problem before.

Thanks in advance
Claudio

PS:sorry for my english.

---

### Post by cltrujil on 2007-10-03
Additionally I can say that sometimes when I boot at the end of the image with the progress bar the image reduces it size, what package should I reinstall?.
Well and the problems with the NO users logged in is still a mistery for me. I would like to know what package should I reinstall too.

Thanks in advance.
Claudio

---

### Post by cltrujil on 2007-10-09
Well, I could fix the problem with graphics removing the new bootscreen and some others look & feel things that I had. 
But I still have the problem with the number of users logged in my machine, all the commands related show NO USERS logged. It is so strange, I have reinstalled the coreutils package but the problem continue. I have reinstalled the kernel package with no result. Well if someone can show me some kind of light about it, how to proceed I would really apreciatte it. I don't know what else I could do.

Well Thank's in advance

Claudio

---

