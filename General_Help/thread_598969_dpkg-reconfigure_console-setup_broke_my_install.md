---
title: "dpkg-reconfigure console-setup broke my install"
date: 2007-10-31
forum: General Help
---

### Post by Sim777 on 2007-10-31
I was in process of attempting to fix reproducing each second messages in logs  
_________________Message from var/log/syslog__________________________________
Oct 29 10:59:57 sim-laptop kernel: [ 2084.302456] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Oct 29 11:00:30 sim-laptop kernel: [ 2110.844754] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
__________________________________________________


and followed suggestion to run "dpkg-reconfigure console-setup" and  select proper keyboard. But it seems I mistakenly selected wrong one. After reboot, system no longer comes up normally. After long "Loading, please wait" following message pops up 

_________________________________________________
check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT /dev/disk/by -uuid/72a550ld-cd34-46ef-a263-dfb1d40a39-6f does not exist
Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-subuntu7) Build-in shell (ash)

(initramfs) _
________________________________________________


If I select recovery, terminal is spammed each second by following message. 
____________________________________
 atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
___________________________________


Is there a way to run that command again from LiveCD? or manually edit area where-ever "dpkg-reconfigure console-setup" saves configuration. 


Please help. ....

I use 7.10 on Dell Inspiron 1501

---

### Post by Sim777 on 2007-11-01
I'm pretty sure it's an easy fix...if only I knew which file to modify.....

---

### Post by perixx on 2007-11-01
Hi...

I can't guarantee if it helps, but you could replace your /etc/X11/xorg.conf file with a backup that you know it worked (if there's any) - or you might try to re-install your desktop. Depends, what Ubuntu-flavor you have, though (I suppose Gnome desktop / Ubuntu?).

Check, if your repositories are set up correctly in /etc/apt/sources.list 
and in bash mode / Terminal type:

```
sudo apt-get ubuntu-desktop
```
(should be the respective command for Gnome-Desktop - use 'xubuntu-desktop' for Xfce or 'kubuntu-desktop' for KDE)

If that won't work because there's already a desktop installed, removing it first with
```
sudo apt-get remove ubuntu-desktop
```
should work, I guess.

Afterwards, type

```
sudo /etc/initd/gdm restart
```


Good luck!

---

### Post by Sim777 on 2007-11-01
Thanks for reply perixx, I will poke around xorg.conf and/or reinstallement of desktop. 
*****

Folks at ubuntu channel on IRC suggested to bootup on liveCD and 'chroot' to my installed directory and run "dpkg-reconfigure console-setup" again. 

After I run it, terminal is full of messages similar to 

```

/var/lib/dpkg/info/console-setup.postinst: 80: cannot create /dev/null: permission denied. 


```  

This is odd because I made sure to become 'su -'

---

### Post by perixx on 2007-11-01
I suppose it's because 'root' has no r/w permissions under Ubuntu?

I'm no expert in changing file permissions on the bash, though...

perixx

---

### Post by perixx on 2007-11-02
maybe this is of help to you ...

> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Oh, did you try to temporarily do a > sudo su ?

regards, 


perixx

---

