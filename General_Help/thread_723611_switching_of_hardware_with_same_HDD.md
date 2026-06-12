---
title: "switching of hardware with same HDD"
date: 2008-03-13
forum: General Help
---

### Post by tehwabbit on 2008-03-13
[I][B][COLOR="Red"]
PROBLEM FIXED

[/COLOR][/B][/I]


Ive recently installed Ubuntu on a spare HDD to use as my portable OS (travelling between homes without carrying a PC)

The system i installed it on was a Intel Quad Core machine and all worked fine and the resolution was quite large.
However i put the hdd into my Pentium 4 machine at my other house expecting it to run pretty much fine but now i cant boot sucessfully into ubuntu :(!!!!

I have used other linux distro's which support switching between pc's and wondered if theres something i can do to make it work (the errors are below[or what i can read of it anyway])

- Something to do with "CPU Frequency not supported"  - roughly, the resolution is rubbish so hard to read.
- an error to do with startX and not being able to initialize.


Im not overly good with Ubuntu but i know i can get into the safe-mode cmd line fine with no problems and wondered if theres any commands i can use to fix my problem, i really need some files :(

---

### Post by Rocket2DMn on 2008-03-13
Moving the drive between different computers means that the video cards and monitors will be different, so the GUI stuff can get screwed up easily.  Maybe you should create different profiles of xorg.conf for your different locations.
Back up the one that works on your quad core system from the recovery mode kernel:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.quadcore
```
Now have it regenerate xorg.conf automatically on your new system at the recovery kernel:
```
dpkg-reconfigure xserver-xorg -phigh
```
Then reboot, you should be good to go.  If not, follow this guide to configure X manually - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
When you have a working xorg.conf for this machine, back that up, too.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.p4
```
(sudo required because I'm assuming you're in the GUI logged in with your standard username.  The commands above require sudo if you are at a normal tty or gnome terminal).

Then when you switch between computers, you need to restore the xorg.conf that works with them:
```
[sudo] cp /etc/X11/xorg.conf.*workingbackup* /etc/X11/xorg.conf
```

---

### Post by tehwabbit on 2008-03-13
Thanks, im now on Ubuntu and accessing my files with a GUI :)

You deserve a cookie :)

---

