---
title: "Changing plymouth and grub resolution in ubuntu 14.04 with nvidia?"
date: 2014-04-22
forum: General Help
---

### Post by nuttzo31 on 2014-04-22
Has anyone managed to be able to get plymouth and grub looking good on trusty?

I have  got it looking good (1920x1080 resolution on plymouth and grub))  on mint 13 and presumably ubuntu 12.04 but trusty doesn't change resolution and behaves the same.

I have tried adding this to etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap"
GRUB_GFXMODE=1920x1080

This to modules
uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap

and framebuffer=y to 
/etc/initramfs-tools/conf.d/splash 

and then updated initramfs and grub but nothing changes in trusty.

Can anyone give me any tips?

edit:
using nvidia-331 drivers.

---

### Post by Steven_Zalek on 2014-04-25
I am experiencing the exact same issue. 

I am using a Lenovo T510 with a NVS3100M graphics card running Xubuntu-14.04_x64 and the NVIDIA-331.38 tested (standard) drivers.

The modifications listed in the previous post have successfully worked on this computer for Xubuntu-12.10_x64, -13.04_x64, and -13.10_x64. They do not work for 14.04_x64.

By implementing JUST the following to etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" [no change here from standard grub file]
GRUB_GFXMODE=1280x800 [appropriate for my graphics card, and worked well with previous editions of (X)ubuntu]

and framebuffer=y to 
/etc/initramfs-tools/conf.d/splash

and NO change to the /etc/initramfs-tools/modules file, I can get a text-only version of plymouth to run, which does cover up the linux start-up notifications.

Any suggestions would be greatly appreciated.

---

### Post by jcottier on 2015-03-06
Try this [http://askubuntu.com/questions/456744/text-gets-displayed-during-boot-after-nvidia-installtion](http://askubuntu.com/questions/456744/text-gets-displayed-during-boot-after-nvidia-installtion)

It worked for me with 14.04.1 and nvidia Quadro K420 and Nvidia driver (from xorg-edgers ppa) 340.76. After a fresh install I got only the Nouveau driver, no propriatry drivers where avaliable at all! After adding the xorg-edgers ppa I lost Plymouth as usual. But this fix works well, takes second or so to fill the (very hi resolution) grub menu screen. I used the max resolution that videoinfo listed.

---

