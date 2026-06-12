---
title: "[SOLVED] Installation on new 250Gigabyte hard drive - Ubuntu 8.04 fresh install"
date: 2008-06-14
forum: General Help
---

### Post by alloftheabove on 2008-06-14
It doesn't work.  When I start my computer after the installation, it gives me grub error 18.

When I use the LiveCd to put the command 
```
fdisk -l
```
I get absolutely nothing.  It simply starts a new line.

Maybe someone has some helpful advice?  I'm pretty sure it's something to do with the hard drive, but of course I probably have no clue what I'm talking about...

---

### Post by wolfen69 on 2008-06-14
Grub Error 18: Selected cylinder exceeds maximum supported by BIOS This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

you could try a BIOS update.

---

### Post by cdtech on 2008-06-14
Try sudo fdisk -l

You may need to reinstall grub.

---

### Post by alloftheabove on 2008-06-14
Here: 

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x014ccd1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30261   243071451   83  Linux
/dev/sda2           30262       30401     1124550    5  Extended
/dev/sda5           30262       30401     1124518+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

---

### Post by alloftheabove on 2008-06-14
Hello?  Anyone out there reading this?

How do you update bios?


BTW: I already tried reinstalling grub.  Didn't work.

---

### Post by rraj.be on 2008-06-14
Just reinstall your GRUB.
Follow the fllowing.

```
Boot into live cd.
```

open terminal

type ```
sudo grub

find /boot/grub/stage1
```

If it returns like hd(x,y)

type 

```
root (x,y)

setup (x)

quit

sudo reboot
```

it will solve your problem.

---

### Post by alloftheabove on 2008-06-14
It was able to find /grub/boot/stage1 before, but now
it can't find it.

EDIT: Nevermind, I tried it, it set it up, but I'm still get grub error 18.

---

### Post by yoman82 on 2008-06-14
Well, what type of BIOS chip are you using?

---

### Post by rraj.be on 2008-06-14
Thenits something with BIOS or hardware cluster size as given in ubuntu DOCUMENTATION.

---

### Post by confused57 on 2008-06-14
> **alloftheabove said:**
> It was able to find /grub/boot/stage1 before, but now
it can't find it.

EDIT: Nevermind, I tried it, it set it up, but I'm still get grub error 18.
Your best bet would be to reinstall Ubuntu, select manual partitioning...delete your current partitions.  Make your root partition (/) approximately 15 Gb, primary, format as ext3, mountpoint  / ; then swap of approx. 1.5 times the size of your ram(mountpoint swap, logical) ; then the rest of your drive make a separate /home partition(mountpoint /home, format as ext3, logical).
Make sure the / partition is at the beginning of the drive.

Here is an excellent partitioning guide:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by alloftheabove on 2008-06-14
I have no clue.

---

### Post by yoman82 on 2008-06-14
Fire Up BIOS, and it should say it by the top of the screen. If not, I would try opening up the Somputer and looking directly at the ship, the name is probably printed on it.

---

### Post by alloftheabove on 2008-06-14
I'm gonna try confused57's idea first.  And I'm pretty sure the name of the bios chip is listed in bios.  I just haven't needed to look at it.  I'll get back when I'm done.

---

### Post by alloftheabove on 2008-06-14
This case is SOLVED!  Thank you confused57!

---

### Post by confused57 on 2008-06-14
> **alloftheabove said:**
> This case is SOLVED!  Thank you confused57!
Glad to have helped, this explains a little more about grub error 18:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

In my opinion, if everything else is working fine(other than grub error 18 ), flashing the bios would be a last resort for me.

---

