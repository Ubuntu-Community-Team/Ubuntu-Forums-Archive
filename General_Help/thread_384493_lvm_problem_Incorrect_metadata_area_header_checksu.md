---
title: "lvm problem: Incorrect metadata area header checksum"
date: 2007-03-14
forum: General Help
---

### Post by Alex99 on 2007-03-14
Hi,
when trying to install a program the terminal tells me there's too little space in a volume. Although there's free space on my hard drive, I'm having problems extending that logical volume.
I'm assuming it's /dev/vg00/opt because the system monitor says there's only 250MB left. There's a lot more in other volumes.
When trying to extend the volume, the terminal says:
```
Incorrect metadata area header checksum
```
When running 
```
vgscan
```
the terminal tells me
```
Found volume group "vg00" using metadata type lvm2
```
I have no idea what this means, but I guess it's the reason that I can't extend /dev/vg00/opt. I need to, however, because I need to install OpenOffice.
Any ideas?

Edit:
It's getting worse: Now I can't boot!


Right after the status bar with the ubuntu logo appears, there's a black screen saying

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty: job control turned off
(initramfs)

If I enter Alt - Ctrl - F1, I get the message: 

Incorrect metadata checksum area header checksum
8logical volume(s) in volume group "vg0" now active
Target filesystem doesn't have /sbin/init

This is an edgy system. The eight volume groups are all the partitions I have got, apart from boot, which is not a volume group. When I start an install cd and enter the recovery mode, I do get a shell that's started from /, but I don't know what to do with it...

---

