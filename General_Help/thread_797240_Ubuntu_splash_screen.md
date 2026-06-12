---
title: "Ubuntu splash screen"
date: 2008-05-17
forum: General Help
---

### Post by eddyr on 2008-05-17
Hi,
I'm having trouble getting pass the Ubuntu splash screen. it leaves me with a progress bar that runs in an infinite loop.

This only happens when i restart the PC from Ubuntu or Windows. The only way i can get into Ubuntu is if i power up the PC. So every time i need to get into Ubuntu, my PC needs to initially be turned off.

Anyone else having this issue?

---

### Post by plucky on 2008-05-17
> **eddyr said:**
> Hi,
I'm having trouble getting pass the Ubuntu splash screen. it leaves me with a progress bar that runs in an infinite loop.

This only happens when i restart the PC from Ubuntu or Windows. The only way i can get into Ubuntu is if i power up the PC. So every time i need to get into Ubuntu, my PC needs to initially be turned off.

Anyone else having this issue?



Edit the menu.lst file and take out the word **quiet** so that you can see what is causing the startup to loop.

To edit the file ```
gksudo gedit /boot/grub/menu.lst
```

Search for the lines that look like this

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

and change it to this 


> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro splash
initrd		/boot/initrd.img-2.6.24-16-generic


I.e remove the word **quiet**

Follow the procedure that causes the problem and it should tell you what it is trying to startup.

Good luck.

---

### Post by eddyr on 2008-05-17
It stops at "waiting for root filesystem"

---

### Post by kbuel on 2008-05-18
mine stops on "waiting for root filesystem" also.  After different lengths of time (up to a minute or two) it will move on though... Still it is annoying and didn't happen in gutsy gibbon

---

### Post by cdtech on 2008-05-18
It's the /boot/grub/menu.lst. Look at the device that it boots too, it probably states something like hda and should be something like sda? (where your boot partition is). Look at sudo fdisk -l to see your drives.

---

### Post by CREEPING DEATH on 2008-05-18
Did you move the hard drive around by chance?

CD

---

### Post by eddyr on 2008-05-18
cdtech: It is one of the devices. 
CREEPING DEATH: I didn't move it.

Would it be an issue with the power supply? maybe it doesn't have sufficient power to power up the hdd?

---

### Post by kbuel on 2008-05-18
> **cdtech said:**
> It's the /boot/grub/menu.lst. Look at the device that it boots too, it probably states something like hda and should be something like sda? (where your boot partition is). Look at sudo fdisk -l to see your drives.


my menu.lst looks like this:
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=62bb3d2e-d3ea-4c3a-8d9d-6d7e96369118 ro splash
initrd          /boot/initrd.img-2.6.24-16-generic
#quiet


and fdisk -l produces this:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50455044

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris


should I have something different in my menu.lst?

---

### Post by kbuel on 2008-05-19
is anyone else experiencing this?

---

### Post by cdtech on 2008-05-19
Personaly I would replace the root=UUID with root=/dev/hda1, just to see how it acks. Thats the same as using the UUID. May help....

Should look like this:
root=/dev/hda1 ro splash

(Linux IDE) hda1 being the same as (GRUB IDE) hd0,0 (first hard drive, first partition).

Linux SCSI - sda1
GRUB SCSI - hd0,0

---

