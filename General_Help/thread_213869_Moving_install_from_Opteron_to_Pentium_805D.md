---
title: "Moving install from Opteron to Pentium 805D"
date: 2006-07-11
forum: General Help
---

### Post by nameiwantistaken on 2006-07-11
I tried running my linux install on a different platform today and it won't go through the boot process.  The final error it gives is /bin/sh: can't access ttyl; job control turned off and then it gives me a command prompt.  Is there an easy way to migrate this install?  Can I reinstall somehow and not lose web, LAMP, hamachi, VNC, EVMSGUI and all of the other programs I have battled to get working?

---

### Post by radiazo on 2006-07-11
you need to install and boot from kernel 386.
after, you probably need to reconfigure your xorg server. use: sudo dpkg-reconfigure xserver-xorg in a terminal.

---

### Post by nameiwantistaken on 2006-07-11
What do you mean by install and boot from kernel 386?  This install was done with the server version of Ubuntu 386 with the GUI layered on it so LAMP would work by default.  I understand the second part.  Some more details would be very appreciated.  Thanks for your help.

---

### Post by RAOF on 2006-07-11
I think that the problem is probably that the root partition has a different name on the new system.  That said, could you post **all** the errors?  That makes it easier :)

---

### Post by radiazo on 2006-07-11
Are you using the default kernel? please confirm that with a "uname -a".

---

### Post by radiazo on 2006-07-11
if that happens, maybe the grub dont found the partition, and the first post indicates an shell error!!

---

### Post by nameiwantistaken on 2006-07-12
Ok here goes, but pardon if this isn't exact.  HOpefully it will give you a better idea.

Uncomplressing linux...ok, bootin gthe kernel.
1717934.656000 ..mp-bios bug:8254 timer not connected to IO-APIC
17179575.868000 PCI:Cannot allocate resource region 3 of device 0000:00:00.0
mdadm: /dev/md0 has been started with 4 drives (my glorious raid array)
mount: mounting /dev/sda1 on /root failed: device or resource busy
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc fialed: No such file or direcotry
Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off.

---

### Post by nameiwantistaken on 2006-07-12
uname -a output is 

Linux (none) 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 unknown

---

### Post by RAOF on 2006-07-12
> **nameiwantistaken said:**
> ...
**mount: mounting /dev/sda1 on /root failed: device or resource busy**
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc fialed: No such file or direcotry
...
There's your problem.  Your root partition isn't on the raid, is it?
It looks to me like your harddrives got renamed in the switch between boxes.  The /dev/sda1 busy makes it look like sda1 is now a part of md0, and is hence busy when you try to mount it on root.

I'd suggest firing up a livecd, and seeing what's what.  What device is your root partition on, what devices make up md0, that sort of thing.

---

### Post by nameiwantistaken on 2006-07-12
Well my setup is a raptor for the OS and 4 300Gb sata's for the array.  I put the raptor on RAID-1 on the motherboard again.  It would be difficult for the Raptor to join the array given that its one tenth the capacity or so I would think.  What should I look for with the live CD?

---

### Post by RAOF on 2006-07-12
Look for which /dev/sd*x* corresponds to your root partition :).  Then you'll want to fix up grub's menu.lst to use that device as the root it passes to the kernel on boot.  

I think.  I didn't think that the kernel would get that far without a working / partition.  But maybe I'm wrong :)

---

### Post by nameiwantistaken on 2006-07-12
I played musical chairs with the sata connections sans the music part and eventually got my Raptor as the first boot.  I set it up again to be the bootable drive by the motherboard and off we go.  I did the reconfigure as suggested and it is working once again.  Now for my next dumb post.  Firewall advice anyone?

---

### Post by RAOF on 2006-07-12
None?  Unless you've want some pretty restrictive rules, a firewall's not going to do anything.  Either it will block ports that nothing's listening on, or it will block something you **want** to have access to.

Basically: if you haven't installed any server daemons, nothing's listening to the internet.  If you **have** installed some server daemons (ssh, apache, whatever), presumably you **want** them to listen to the internet :).

Unless you want to do something quite fancy (block access to only a limitied set of ip addresses, port knocking, or something similar) the only thing a firewall does is get in the way of what you want.

---

### Post by nameiwantistaken on 2006-07-12
Well basically I only want 5.x.x.x and 192.168.0.x addresses to be able to connect to vnc.

---

### Post by RAOF on 2006-07-12
firestarter's meant to be a good front-end to the iptables firewall?  That's in the repositories.

---

