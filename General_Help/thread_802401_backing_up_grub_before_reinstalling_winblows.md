---
title: "backing up grub before reinstalling winblows"
date: 2008-05-21
forum: General Help
---

### Post by randini on 2008-05-21
I tried searching, but wasn't able to find the answer to my question like I usually can (hence this is my first post here in over a year as a member).

I've FUBAR'ed my winblows XP installation and am going to format it and reinstall XP. Last time I did this, I had a difficult time restoring Grub. So this time I figured that I would try and backup Grub before hand, and hopefully make a boot disk with it that would reinstall grub just the way I have it now, after XP is done. 

Not sure what info I need to post to get the help I need, but I'm on a Toshiba Tecra M2v laptop (only bootable devices are the HDD, ODD and an SDcard reader) dualbooting Ubuntu 7.10 and Windows XP. 

output of fstab -l:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2854    22924723+   7  HPFS/NTFS
/dev/sda2            2855        2916      498015   82  Linux swap / Solaris
/dev/sda3            2917       13112    81899370    f  W95 Ext'd (LBA)
/dev/sda4           13113       14593    11896132+  83  Linux
/dev/sda5            2917       13112    81899338+   7  HPFS/NTFS

output of grub> find /boot/grub/stage1
 (hd0,3)

Thanks in advance.

---

### Post by fsmithred on 2008-05-22
Several ways to do it are shown on this page:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by danwood76 on 2008-05-22
The actual grub files are stored on your linux partition, so as long as you are not re formatting that everything will be the same.

You just then, after the XP install, reinstall grub to the MBR and everything will be back to how it was.

---

