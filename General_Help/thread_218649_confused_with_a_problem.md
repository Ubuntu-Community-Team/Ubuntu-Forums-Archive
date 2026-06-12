---
title: "confused with a problem"
date: 2006-07-18
forum: General Help
---

### Post by grimm_will on 2006-07-18
So I run windows and linux on the same computer on differnt hard drives. I am much more skilled with windows so when my harddrive was not being recognized as ultra dma, I tried with success to get windows to figure it out it was by switching primary and slave harddrives around. Windows now works.
Ubuntu kinda does. Grub couldn't boot me back into linux. I went in with a live disk to see what drives are called what (hda hdd...) Then I went back to grub and edited the boot command replacing hdb with hdd. I was able to load Ubuntu. However linux doesn't mount my  ext3 partition (where everything linux is, except swap ofcourse). I can still use koquerer to browse it though (no idea why I can). Anyway I think I need to mess with my fstab, but I don't know if that is all. I am rather unsure on what all needs to be done. 

I hope this is posted in the right spot. thanks

---

### Post by ciscosurfer on 2006-07-18
Run fdisk again when in Ubuntu.  Run it like this```
sudo fdisk -l    <------ that's a lower case L, not the number 1
```More than likely if you've installed Ubuntu to your second drive, then Grub, your kernel, etc., should be located on the first partition not the fourth (hdb1 = second hard drive, first partition; hdd = second hard drive, fourth partition) If you don't want to mess with your fstab and you don't have much on your Ubuntu system that you wouldn't care losing, try reinstalling Ubuntu from the live CD again and the Automagic script should take care of the rest.

---

