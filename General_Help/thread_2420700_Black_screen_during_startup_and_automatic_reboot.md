---
title: "Black screen during startup and automatic reboot"
date: 2019-06-09
forum: General Help
---

### Post by Atalanttore on 2019-06-09
Hi

On a notebook with Ubuntu 18.04.2 (x86, 32 bit, see [lshw output]("https://pastebin.com/dGvCbCZf")) the boot process has been causing problems since a few days.

  Boot problem in detail:
  
[LIST=1]
[*]On startup no grub menu appears. 
[*]The dark purple background typical for Ubuntu **without** any Ubuntu logo or text appears for several seconds. 
[*]The screen briefly turns black and the notebook restarts automatically. 
[*]The grub menu appears. 
[*]I choose "Ubuntu". 
[*]Ubuntu searches for file system errors. 
[*]Ubuntu boots up. 
[*]The usual Unity 7 desktop appears after a while 
[/LIST]


  After shutting down and turning on again, the process starts again from the beginning. See [syslog]("https://pastebin.com/t7EPFr9r").

  What is the reason for this problem and how can it be solved?

Regards,
Atalanttore

---

### Post by Atalanttore on 2019-06-10
Adding following line to `/etc/default/grub`
```
GRUB_GFXPAYLOAD_LINUX=text
```
and update grub with
```
sudo update-grub
```
solved the problem.

See [Ubuntu bug report 1724639]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639")

Regards,
Atalanttore

---

