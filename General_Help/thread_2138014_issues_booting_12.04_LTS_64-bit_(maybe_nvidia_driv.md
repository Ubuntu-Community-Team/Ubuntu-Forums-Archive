---
title: "issues booting 12.04 LTS 64-bit (maybe nvidia drivers?)"
date: 2013-04-22
forum: General Help
---

### Post by enchevetrement on 2013-04-22
Hello!


I'm having problems booting Ubuntu 12.04 LTS 64-bit since kernel updates about a week ago.  It is on an Acer Aspire 5755G, IntelCore i5 2.4 GHz, nVidia graphics card, 8 GB RAM.


This happens when I boot first time around:


1. purple screen for some time
2. black screen
3. the (USB-connected) printer makes the 'test noise' it always does when the computer starts up  (apologies for my lack of technical vocabulary)
4. nothing more happens, the black screen remains (not lit-up)


If I then do a hard re-boot:
5. grub menu appears
6. choose recovery mode
7. choose to boot normally
8. everything is fine, except graphical effects and external monitor


 I believe it could be related to the driver/s for the nvidia graphics card, based on similar but not identical issues posted in this forum.  I cannot find any drivers in jockey-gtk.


In any case, any help or advice would be very much appreciated!  Quite a beginner, so just let me know what info you need.  

Thanks,
Cc

---

### Post by enchevetrement on 2013-04-25
Update: I "solved" this by installing 12.10 from scratch and then not applying any of the updates.  However, I believe (please correct me if I'm wrong) that this "solution" entails essentially removing some of the recent security updates, so it is probably not recommendable per se.

---

### Post by gordintoronto on 2013-04-25
Safe Computing says: do apply updates.

When you turn on a computer, lean on the shift key to make sure the Grub menu appears. If you install a kernel update, you still can choose the older kernel from Grub.

Have you installed the Additional Driver for your video card? It's in Software Center/Software Sources, I use nvidia-current.

---

