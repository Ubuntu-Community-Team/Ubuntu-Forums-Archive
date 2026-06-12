---
title: "Ubuntu 12.10 Black Screen After First Boot Up"
date: 2013-01-16
forum: General Help
---

### Post by fobos3 on 2013-01-16
Hi

I just reinstalled my OS and I get a black screen before it get into GRUB(or whatever manager it is using). The weird thing is that after I press ctrl+alt+del and the computer restarts it boots normally. Any ideas? Has anyone experienced the same problem.

Regards

---

### Post by oldfred on 2013-01-17
You may just need to change grubs gfxmode.

       Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

    
       Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768


       
 gksudo gedit /etc/default/grub
sudo update-grub

---

