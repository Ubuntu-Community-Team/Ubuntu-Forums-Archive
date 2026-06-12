---
title: "Ubuntu 7.10 Boot problems"
date: 2008-03-13
forum: General Help
---

### Post by dodgeemegee on 2008-03-13
Hi!
I have had Ubuntu 7.10 installed on my HP pavilion 8960 for 4 or 5 days and it has been booting fine.  however, now when I boot it, I get the normal orange gauge, which completes until about 2mm from the end, then I get a white text on black screen which seems to show what is happening in boot up:
*Acivating swapfile swap...                                                 [ OK ]
$mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done.
* Checking minimum space in /tmp...                                  [ OK ]
* Configuring network interfaces ....                                   [ OK ]

                                            etc...

*  Starting powernowd...
/etc/rc2.d/s20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufre
q/scaling_governor: Directory nonexistent
* CPU frequency scaling not supported

* Starting ConsoleKit dqemn console-kit-daemon               [ OK ]
* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon      [ OK ]
* Starting DHCP D-Bus daemon dhcdbd                                [ OK ]
* Starting Bluetooth services                                                      _

Then I get something like a command prompt but unresponsive.   I can start a gui using recovery mode and typing exec gdm-this seems to work fairly normally, but ndiswrapper dosn't repond to -l   (the command to list all installed drivers).  This was the last thing I was doing in linux before the problem - trying to get my wireless adapter to work using ndiswrapper (see [http://ubuntuforums.org/showthread.php?t=720219](http://ubuntuforums.org/showthread.php?t=720219)).  If, in recovery mode, I try to use xstart, it works, but everything is weird, probably because I am logged on as root.  Using exec gnome-session gives the following error:

(gnome-session:4241): Gtk-WARNING **: cannot open display:
init: rcS-sulogin main process (4239) terminated with status 1

I then get an unresponsive command prompt-like line.

Please provide basic steps as I am very new to Linux.

---

### Post by wblancqu on 2008-03-13
edit file /etc/init.d/bluetooth (with administrator rights -> sudo). Add
```
exit 0;
```
at the beginning of the file. This will disable bluetooth but bypass the hang. Wait for a kernel fix for this issue.

Good luck

---

### Post by dodgeemegee on 2008-03-13
Thanks for the reply!
I did what you said, though I'm not sure correctly. These are the first lines of my bluetooth file:
```

# exit 0;
#! /bin/hash
### BEGIN INIT INFO
```

When I start up now, I get the same screen as before, but with this error after Starting bluetooth services:
test: 277: ==: unexpected operator

The problem is probably with where or how I entered the new code.

---

### Post by dodgeemegee on 2008-03-13
Don't worry, I worked it out.  Got rid of the hash and it now starts fine.  Thanks Heaps!

---

