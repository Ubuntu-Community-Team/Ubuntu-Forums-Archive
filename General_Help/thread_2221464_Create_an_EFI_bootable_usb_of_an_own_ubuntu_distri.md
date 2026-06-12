---
title: "Create an EFI bootable usb of an own ubuntu distribution"
date: 2014-05-02
forum: General Help
---

### Post by ann_ht3 on 2014-05-02
I have created an own Ubuntu distribution that I want to boot from a USB on my MAC. When using the standard 64bit-Ubuntu-iso from the Ubuntu website, it  boots. However, when doing the exact same thing with the iso file  containing my own distribution it does not work, and it appears to only  support legacy boot. But the OS I created has the /sys/firmware/efi folder,  so I know it supports EFI. 

I have tried making the iso using both Relinux and remastersys.

  I have looked at the differences between the two ISO files, and have  seen that the standard ubuntu has an EFI/BOOT folder containing  grubx64.efi and BOOTx64.EFI, and also has a boot folder which doesn't  exist in the other file. I have tried to copy these two directories, the EFI  and boot folder into my USB after installing my ubuntu distribution on it, but it didn't work.

  My questions are:
  
[LIST]
[*]How can I get these two folders to appear on the usb stick after installation - using my own iso file? 
[*]Or how can I otherwise make an iso of my distribution so that it supports EFI boot? 
[/LIST]

---

### Post by Leonardvb on 2014-10-01
**[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)**


ReEFIt is the peace of software you are looking for , read more on it with the link

video tut here : [https://www.youtube.com/watch?v=-EVx8p2MK7I](https://www.youtube.com/watch?v=-EVx8p2MK7I)

---

