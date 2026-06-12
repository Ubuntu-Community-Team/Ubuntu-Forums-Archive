---
title: "fried another computer... need help"
date: 2007-12-27
forum: General Help
---

### Post by heyzuphowsitgoin on 2007-12-27
ok so i was trying to install ubuntu on my grandfathers computer on an external hard drive and i made sure it was installing on the external hard drive. When it was done, i restarted the computer, took the hd out, and it said loading grub, then grub error could not load or somthing like that. I cant figure out how or why grub loaded on the computer, and the external hard drive is unreadable too. I need windows to boot up, will someone please help?

---

### Post by gilf on 2007-12-27
Grub works in two stages -- the first is at the beginning of your main hard drive, in something called the MBR or master boot record. It hen jumps to the linux home partition to complete its actions. Since that second location was removed from the computer (you said you removed the external hard drive) it is left hanging with nowhere to go.

Plug that drive back in. If you are set up to dual boot, you should then see the normal Grub boot screen giving you a choice of operating systems. Hit the down arrow until you get to windows to boot into that operating system.

Please tell us exactly what you see when you boot if this doesn't work

---

### Post by meierfra on 2007-12-27
Well it seems grub installed to the MBR of the internal drive, even though you told it to install to the external drive.

**Case 1) You  are able to boot into Ubuntu when the external drive is plugged in.**

Then  click on "DualTwo" in my signature for  instructions how to install grub to the external drive and restore the MBR of the internal drive.

**Case 2)   You  are not  able to boot into Ubuntu when the external drive is plugged in**

Does the Grub Menu appear at boot up?    

Boot from the Ubuntu LiveCD, Go to Places->Computer  and double click on  the icon for the Ubuntu Partition to see whether you can access the files on the Ubuntu Partition.

Then open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```
and

```
cat /media/disk/boot/grub/menu.lst
```

This output will enable us to give you detailed instruction how to fix your problem

** If you just want  to  quickly  boot into Windows: **

click on FixMBR in my signature for instruction how to  restore the MBR of the internal drive

---

