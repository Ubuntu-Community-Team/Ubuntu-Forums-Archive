---
title: "win 7, ubuntu 12.04 dual boot - ubuntu 12.04 doesn't start most of the time"
date: 2013-04-21
forum: General Help
---

### Post by trojanworrier on 2013-04-21
Hi, I'm unable to start ubuntu 12.04 on my laptop most of the time (Even without dual boot, i.e. no win 7 present). Ubuntu works fine if I install any version equal to or less than 10.04.

currently I've installed Ubuntu 12.04 dual boot. Most of the time ubuntu doesn't start and hungs up at the black screen after i select "ubuntu" from the grub (since I've installed ubuntu 12.04 & Win 7). Win 7 runs fine without any issues. Attached file shows h/w that's installed in my laptop.

How to fix this issue?

Thanks all for your help!

---

### Post by carl4926 on 2013-04-21
Can I suggest you try Linux Mint Mate edition
v.13 is equal to Ubuntu 12.04
Or try kubuntu 12.04 or 12.10 and be sure to disable desktop effects

---

### Post by trojanworrier on 2013-04-22
Hi is there a way to fix this instead of installing mint or kubuntu?

---

### Post by carl4926 on 2013-04-22
Use fallback mode

---

### Post by oldfred on 2013-04-22
Fallback is gnome-panel and I use it.
 gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

How much RAM? If you do not have a lot you can just install the Kubuntu or Lubuntu desktops to your current install. 

 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install ubuntu-desktop

And if you do not want full desktop which includes all the packages you can just install the DE -Desktop environment.

---

