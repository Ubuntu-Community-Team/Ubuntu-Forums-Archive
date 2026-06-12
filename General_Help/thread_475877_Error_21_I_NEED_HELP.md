---
title: "Error 21 I NEED HELP"
date: 2007-06-16
forum: General Help
---

### Post by ChopperX on 2007-06-16
Ok i installed Ubuntu using the boot cd and i installed it onto an external hard drive. I restart my pc and it goes Grub Error 21 or whatever it means. Yes i am a newbie at linux

---

### Post by merlinus on 2007-06-16
This may help:

[http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives](http://ubuntuforums.org/showthread.php?t=474734&highlight=two+hard+drives)

-merlin

---

### Post by ChopperX on 2007-06-16
well i followed that code in terminal but it gives me an error 27

---

### Post by merlinus on 2007-06-16
In that case, it might be useful to post each of the following:

```

sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab

```

-merlin

---

### Post by ChopperX on 2007-06-16
how do i do that. In terminal? What do i type?

---

### Post by merlinus on 2007-06-16
Everything in Code:

is what you type in the terminal, one command at a time.

Best to copy-and-paste.

-merlin

---

### Post by ChopperX on 2007-06-16
Well heres the code right from Terminal. I just want to dual boot but right now im stuck in Ubuntu. But its still cool :D

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3655    29358756    7  HPFS/NTFS
/dev/hda2            3656       10327    53592840    f  W95 Ext'd (LBA)
/dev/hda3           15427       19457    32379007+   7  HPFS/NTFS
/dev/hda5            3656       10327    53592808+   7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7165    57552831   83  Linux
/dev/sdb2            7166        7476     2498107+   5  Extended
/dev/sdb5            7166        7476     2498076   82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-06-16
It would seem that you are running ubuntu from the live cd.  That is why the last two commands did not give anything useful.

You will need to mount your linux and windows partitions.

This may help:

[http://users.bigpond.net.au/hermanzone/p10.htm#Filesystem_mounting_basics](http://users.bigpond.net.au/hermanzone/p10.htm#Filesystem_mounting_basics)

-merlin

---

### Post by ChopperX on 2007-06-16
well this seems too complicated for me. Is it easier if i remove windows and just use linux off the C Drive?

---

### Post by logos34 on 2007-06-16
Sounds like grub is installed on the external drive sdb and you are booting to it but grub is confused because menu.lst probably has sdb designated ('hd1)', which is what it was at install time.  The minute you switch the bios to boot to the usb drive it becomes '(hd0)' -- grub uses bios 'calls' to figure out where the root parition is at startup.  This is a common problem with installing on usb drives.  I think you just need to edit menu.lst and device.map

---

### Post by ChopperX on 2007-06-16
well im going to completeply remove windows and just use this as a linux ubuntu pc. I already have a PC laptop running windows. But how do i do this?

---

### Post by logos34 on 2007-06-16
why not just just use Gparted on the ubuntu live cd to wipe wndows off the internal hard drive.. you could also (re)install ubuntu there and use the external for backup and data storage.

---

### Post by merlinus on 2007-06-16
Boot from the live cd.  When it is up-and-running, click the Install icon on the desktop.

At the partitioning screen, select Use Entire Disk, or something to that effect.

-merlin

---

### Post by ChopperX on 2007-06-16
ok this is upsetting me. Now i have like a dead os or something. My hd is messed up I really dont know

This is the new error. It says Kernel Panic during startup. This is what it really says

[   0.623104] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by merlinus on 2007-06-16
Are you booting from the live cd?

-merlin

---

### Post by ChopperX on 2007-06-16
its the only way to get on my computer. I lost windows as far as i know and the only way i can acess anything that has color is ubuntu from live cd

---

### Post by merlinus on 2007-06-16
When the live cd is up-and-running, can you select Install from the desktop icon?

If so, when you get to the partitioning screen, select Use Entire Disk.  Then ubuntu will overwrite everything on your hard disk, and install itself.

This will probably solve all of your problems.....

-merlin

---

### Post by ChopperX on 2007-06-16
well currently i am backing up everything personal of mine then i will do as u say. Once i backup everything it doesnt matter

---

### Post by ChopperX on 2007-06-17
Alright i got it working. Its the only operating i have now but its running fine. Thanks alot you guys for your help :D

---

