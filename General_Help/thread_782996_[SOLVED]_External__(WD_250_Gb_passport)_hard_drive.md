---
title: "[SOLVED] External  (WD 250 Gb passport) hard drive"
date: 2008-05-05
forum: General Help
---

### Post by cosine352 on 2008-05-05
Hi friends,
I am new to ubuntu. I am loving it. 
I have one problem. I can not mount WD 250 Gb passport USB external hard drive automatically. The hard drive is USB powered (ie no external power supply). 
I usually type 
> mount -t vfat /dev/sdc1 /mnt/usbdrive

In this way in terminal if I go to the 
> cd /mnt/usbdrive
I can see the files and can open them from terminal by typing
> gnome-open "file_name"

But the problem is it takes lot of time to open any file. And also I can not open the gnome file browser (it freezes when I try to open it).

I think the problem may be due to the power management of my USB drive. I have USB 1 drives. 

Please help me.
Thanks in advance.

---

### Post by Jeff Beezy on 2008-05-05
hmmm, mine auto mounts and shows up on my desktop. are you using hardy?

---

### Post by cosine352 on 2008-05-05
Thanks for quick reply Jeff. 
I am using Ubuntu 7.10 Gutsy.

---

### Post by cosine352 on 2008-05-05
anyone ???????

---

### Post by yorkie on 2008-05-05
go to Applications>system tools>configuration editor
 when widow opens click on Apps>nautilus> desktop look for volumes_visible 
 highlight this then check in box to enable
 this will show any drives on your system 
 plug your hard drive in it can take a few seconds to show you WD drive 
  one more thing  are you plugging in your wd drive directly into your pc/laptop
  or using a hub I had problems with mine using a hub if its not a powered one
  hope this helps

---

### Post by cosine352 on 2008-05-05
Thanks yorkie,
I will give it a try and post my results.

---

### Post by cosine352 on 2008-05-06
> go to Applications>system tools>configuration editor
when widow opens click on Apps>nautilus> desktop look for volumes_visible
highlight this then check in box to enable
this will show any drives on your system
plug your hard drive in it can take a few seconds to show you WD drive
one more thing are you plugging in your wd drive directly into your pc/laptop
or using a hub I had problems with mine using a hub if its not a powered one
hope this helps

I already have this configuration. So still no luck. :(

---

### Post by cosine352 on 2008-07-23
I have reformated it to ext3 and working perfect.

---

