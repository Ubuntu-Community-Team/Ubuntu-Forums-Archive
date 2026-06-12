---
title: "Installed Ubuntu on external drive.. during boot GRUB error 17"
date: 2007-01-24
forum: General Help
---

### Post by presbp on 2007-01-24
I installed GRUB and Ubuntu 6.10 onto my external hard drive.  I have the drive divided into 3 partitions.. 1 for backup Windows files 2nd for Ubuntu and 3rd for the swap file.  If I don't have the drive connected it automatically loads Windows and there is no presence of GRUB.  When I have the external drive plugged up I can go to the BIOS and set that drive to boot before the internal drive and when I do that it says 
 
 'grub stage 1.5 loading'      
   
 then something like 'grub error 17'  

 the external hard drive is NTFS apart from the ubuntu and swap partitions.  I don't know if that is the problem.  Do I need to create another partition and set it to /boot and then install grub to it?? 

What should I do.. I do not want GRUB on my Windows hard drive (internal).
Thank you.  Please try to get around to answering.

---

### Post by Choad on 2007-01-24
> **presbp said:**
> I installed GRUB and Ubuntu 6.10 onto my external hard drive.  I have the drive divided into 3 partitions.. 1 for backup Windows files 2nd for Ubuntu and 3rd for the swap file.  If I don't have the drive connected it automatically loads Windows and there is no presence of GRUB.  When I have the external drive plugged up I can go to the BIOS and set that drive to boot before the internal drive and when I do that it says 
 
 'grub stage 1.5 loading'      
   
 then something like 'grub error 17'  

 the external hard drive is NTFS apart from the ubuntu and swap partitions.  I don't know if that is the problem.  Do I need to create another partition and set it to /boot and then install grub to it?? 

What should I do.. I do not want GRUB on my Windows hard drive (internal).
Thank you.  Please try to get around to answering.
put in the external hard disk, set your bios to boot from the external disk first, put in the ubuntu cd and reboot so it loads up the live environment

open a terminal (apps >: accessories> terminal)

type the following commands:

sudo grub
(you now go to a grub console)

find /boot/grub/stage1
(it will probably return something like found (hd1,0). i will assume it is that)

root (hd1,0)
setup (hd1)
quit


obviosuly if it returns something different, use the different value

---

### Post by presbp on 2007-01-25
that didn't work.  I will try it again just to make sure.

---

### Post by presbp on 2007-01-25
this is what I did 

grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
 
I am going to try booting again.

---

