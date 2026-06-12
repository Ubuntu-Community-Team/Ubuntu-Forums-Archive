---
title: "UBuntu and AV5"
date: 2013-07-13
forum: General Help
---

### Post by chkneater on 2013-07-13
I have AV5 installed as the main system and just installed US12.04 and the grub is giving "unknown filesystem" and dropping to grub rescue.

Anyone have ideas??  I don't want to chroot or remove US12.04 to get things working again.  Thanks for your helps!!

Well I've managed to get the AV5 partition booting again, haven't tried ubuntu yet, too scared.

I noticed there was no grub in the US12.04 boot dir so I used the commands: 

grub-mkconfig            # regenerate grub.cfg
grub-install /dev/sda  #Install grub bootloader on /dev/sda

to get things back to normal.  Now AV5 is on sda1, and US is on sda3.  

Having said that, normally the grub.cfg on sda1 has all the menu entries and sda3 has just that partitions menu entries on it.  

However, after using the same commands I've used before, now sda3 (ubuntu) contains all the menu entries of the disk and sda1 has just that partitions entries.  

I have the option of restoring things back to normal using remastersys grub restore which lets me choose where to put grub, but I want to know if this grub config as it is now might work?

Anybody with experience with multi installs?  I eventually want to add AV6 or something new also, but for now I want to be able to mount into BOTH my partitions.

So far all I've tried has failed, so I'm going to delete the AV5 partition completely, and see if I can get 12.04 to boot then.  If so, and things go well I'm going to try reinstalling AV5 and see what happens.

Does anybody have any advice how to get Ubuntu to get along with AV5 or 6?

---

