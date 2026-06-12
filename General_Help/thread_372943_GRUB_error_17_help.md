---
title: "GRUB error 17 help"
date: 2007-02-28
forum: General Help
---

### Post by SmiLey497 on 2007-02-28
I just deleted windows,  but when i try to go into ubuntu it gives me ERROR 17: Cannot mount selected partition, 

here is what running  sudo fdisk -l in the terminal read out

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       28900   232139218+  83  Linux
/dev/sda3           28901       29251     2819407+   5  Extended
/dev/sda5           28901       29251     2819376   82  Linux swap / Solaris

---

### Post by SmiLey497 on 2007-02-28
bump

---

### Post by SmiLey497 on 2007-03-01
somebody help please

---

### Post by SmiLey497 on 2007-03-01
when i check gparted it says my linux drive is not mounted, how do i mount it?

---

### Post by confused57 on 2007-03-01
> **SmiLey497 said:**
> when i run find /boot/grub/stage1, it gives me hd(0,1) even though linux is on sda2, i need help here
You could "experiment" with different settings for root...at the grub menu, highlight your Ubuntu entry, press "e" to edit, change root from (hd0,1) to (hd0,0), then press "b" to boot.
If the above doesn't work, you might also need to change the kernel line to root=/dev/sda1...these changes are temporary, so you're not hurting anything, but you might be able to find a combination that will boot Ubuntu...if you do, you can make it permanent in your /boot/grub/menu.lst.

---

### Post by SmiLey497 on 2007-03-01
i checked and it said root(hd0,2), i think the problems is that linux is not mounted

---

### Post by SmiLey497 on 2007-03-01
> **confused57 said:**
> You could "experiment" with different settings for root...at the grub menu, highlight your Ubuntu entry, press "e" to edit, change root from (hd0,1) to (hd0,0), then press "b" to boot.
If the above doesn't work, you might also need to change the kernel line to root=/dev/sda1...these changes are temporary, so you're not hurting anything, but you might be able to find a combination that will boot Ubuntu...if you do, you can make it permanent in your /boot/grub/menu.lst.

i tried doing wat you said it, the kubuntu splash screen popped up like it was goin to start than it went black and i got busybox /bin/sh: can't access tty; job contro turned off

---

### Post by confused57 on 2007-03-01
> **SmiLey497 said:**
> i tried doing wat you said it, the kubuntu splash screen popped up like it was goin to start than it went black and i got busybox /bin/sh: can't access tty; job contro turned off
Windows must have been on sda1, did you just delete Windows & now it's unallocated space or did you resize your root partition, adding to the root partition?

If it's free space, you might be able to format it ext3, with the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
then your root partition will again be (hd0,1) or the second partition 

I'm not sure really what you need to do...you might want to wait to see if someone else has an idea.

---

### Post by SmiLey497 on 2007-03-02
> **confused57 said:**
> Windows must have been on sda1, did you just delete Windows & now it's unallocated space or did you resize your root partition, adding to the root partition?

If it's free space, you might be able to format it ext3, with the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
then your root partition will again be (hd0,1) or the second partition 

I'm not sure really what you need to do...you might want to wait to see if someone else has an idea.

i deleted windows and added the space to my ext3 partition

---

