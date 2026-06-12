---
title: "can you boot ubuntu to dos?"
date: 2006-08-14
forum: General Help
---

### Post by ron obine on 2006-08-14
I only have dos on my computer. The ubuntu cd will not boot.  I get the menu. I checked the cd. It says its loading but locks up the computer....Help Ron obine

---

### Post by Ramses de Norre on 2006-08-14
Have you tried the alternate cd? What are your computer's specs?

---

### Post by Mr_Congeniality on 2006-08-14
you may need to specifiy to the GRUB Boot Loader what kind of partition the DOS is (it isn't going to auto-detect, I don't think.)

Then make sure it is aimed to boot at the right partition, so if DOS was your 1st partition (which is probably how it's supposed to be), then you should put /dev/sda1 (if you have a SATA device and it's on your first hard drive.)  It goes like this: /dev/(S=Sata H=IDE)D(A=1st hard drive, B=2nd Hard Drive, etc.)(Partition Number Follows.)  So if you had a IDE Hard drive that was your computer's 3rd hard drive with DOS on the 4th partition, it would be /dev/hdc4.

---

### Post by Mr_Congeniality on 2006-08-14
Oh yeah, do you think you can post your /boot/grub/menu.lst file on here?  I might be able to help you more.

---

