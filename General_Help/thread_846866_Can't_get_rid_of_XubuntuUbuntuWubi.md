---
title: "Can't get rid of Xubuntu/Ubuntu/Wubi"
date: 2008-07-01
forum: General Help
---

### Post by MWK-ATL on 2008-07-01
So I've tried everything I can to rid myself of all vestiges of Wubi and Xubuntu, but I still get the dual boot screen when booting.  Please, would someone explain IN ABSOLUTE KINDERGARTEN TERMS what I have to do to get rid of this?

---

### Post by ibutho on 2008-07-01
If you mean grub, then download the [Super Grub Disk]("http://www.supergrubdisk.org") and use it to restore the Windows bootloader.

---

### Post by MWK-ATL on 2008-07-02
I've got grub disk, had to use it before for a partition issue (MBR rebuild) but haven't used it for this. Do you know the command?  Sorry I'm an idiot, thanks for all your help!

---

### Post by ibutho on 2008-07-02
When you run the disk, you are presented with several options. Choose the option to restore the Windows boot loader. There are other ways to get rid of grub. If you have a Win 98, ME, DOS or FreeDOS disk, you can boot using the disk and run "fdisk /mbr". If you have an XP disk, you can run it, get into rescue mode and enter "fixmbr".

---

### Post by ago on 2008-07-02
[https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by TheTrlak on 2008-07-02
I just can not seem to be able to remove mine either, i dont have the option with edit to remove them from my loader. Nor are htere any traces that I can find in my regedit. I am rather confused at this point.

---

