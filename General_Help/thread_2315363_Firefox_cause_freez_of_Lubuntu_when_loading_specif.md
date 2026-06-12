---
title: "Firefox cause freez of Lubuntu when loading specific URL"
date: 2016-02-28
forum: General Help
---

### Post by fillip1 on 2016-02-28
When i try to load [https://openclipart.org/detail/28407/fleur-de-lis](https://openclipart.org/detail/28407/fleur-de-lis) Lubuntu is freez.
Keyboard is unresponsive (NumLock LED don't change state (shine) if pres NumLock key).
Mouse is working/moving when click nothing happens.

 I have to hard reboot. Any crash report is show after reboot.
I repeated it three times, each time with the same result.
Once it happens also on [https://openclipart.org/detail/225107/speaker](https://openclipart.org/detail/225107/speaker) .

DistroRelease: Lubuntu 15.10
Linux 4.2.0-30-generic i686
FF 44.0.2
[launchpad.net/+bug/1550882]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1550882")

---

### Post by claracc on 2016-02-28
Ubuntu - gnome 14.04.04 running, opening the forementioned link with firefox 44.02, not
any problem of freezing ( I mean not firefox fault).

Have you tried to run ```
top
``` command in xterm while opening the link to see what is happening (perhaps you got out of ram or there is a lot of load for the processor), also, you can try to see some of the /var/log/ files to see if it is something wrong with system? i.e.: dmesg, kern.log or Xorg.0.log in system events.

---

### Post by X-RED_Tech on 2016-02-28
The page has nothing special so the problem must be somewhere else.

---

### Post by fillip1 on 2016-02-28
top is freeze too. Before freeze I don't see anything odd.

It seems freeze is occurs only if I'm logged in to my account on openclipart.

With log files I'm not familiar with (I discovered nothing exciting there).

Kernel.log: [http://paste.ubuntu.com/15229213/](http://paste.ubuntu.com/15229213/)
xorg.0.log: [http://paste.ubuntu.com/15229219/](http://paste.ubuntu.com/15229219/)
dmesg.log: [http://paste.ubuntu.com/15229224/](http://paste.ubuntu.com/15229224/)

---

### Post by claracc on 2016-02-28
One of the more probable culprits use to be the graphic card and its drivers.

You can post here your hardware specifications ( cpu, ram , hdd, graphic card) to
see if some of them can give problems.

I have found these threads

 [http://ubuntuforums.org/showthread.php?t=2305105&goto=newpost/](http://ubuntuforums.org/showthread.php?t=2305105&goto=newpost/) 
[http://askubuntu.com/questions/292633/lubuntu-13-04-freezes-when-starting-firefox](http://askubuntu.com/questions/292633/lubuntu-13-04-freezes-when-starting-firefox)
[http://ubuntuforums.org/showthread.php?t=2228285](http://ubuntuforums.org/showthread.php?t=2228285)

that could give you some clues

---

### Post by fillip1 on 2016-02-28
I use integrate Intel grpahic: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller]) Dirver: driver=i915 xserver-xorg-video-intel 2:2.99.917+git20150808-0ubuntu4
RAM: 1.5 GB
CPU: Intel Pentium 4 3.00GHz

---

