---
title: "Booting 2 linux partitions with Grub"
date: 2005-08-28
forum: General Help
---

### Post by josir on 2005-08-28
Hi folks,
I am converting my Mandrake system to Ubuntu.
I installed Ubuntu on hda without hdb connected. The installation runs smooth.
After that, I attached the hdb (with Mandrake)

Now I want to boot from hda with a grub menu but this my first grub attempt.

I edit menu.lst and add the following menu item:

title		Mandrake
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.8.1-10mdk root=/dev/hdb1 ro splash
initrd		/boot/initrd-2.6.8.1-10mdk.img
savedefault
boot

After that, I tap 'update-grub'
When I edit the menu.lst again, the Mandrake menu item disapears. ](*,)  
What am I doing wrong ?

Thanks in advance,
Josir

---

### Post by jpkotta on 2005-08-28
You should have the same /boot for both distributions, i.e. the Mandriva kernel and Ubuntu kernel are both in the same directory.  Maybe there is a way around it, but you should also have /boot on it's own partition (it shouldn't matter which hd you put it on).  Your menu.lst entry looks good as far as I can tell.  When you're satisfied with menu.lst, run ```
sudo grub-install --root-directory=/boot /dev/hda
``` assuming that you're booting from /dev/hda.  Gentoo has some good GRUB info in their handbook.

---

### Post by josir on 2005-08-28
Hi jpkotta, this is not necessary. I found the problem!

My mistake was 'update-grub' command: I thought that I need this command in order 
to update the grub, like in lilo. But this command just erase my menuitens, creating a default menu.lst.
When I update the menu.lst and DON'T run update-grub, the configuration works.
I extend this approach and now have Ubuntu, Mandrake 10 and Red Hat controlled by just one grub instalation.
Thanks for your attention anyway!
Health and Freedom,
Josir.

---

