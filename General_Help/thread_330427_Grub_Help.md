---
title: "Grub Help"
date: 2007-01-03
forum: General Help
---

### Post by avantgardaclue on 2007-01-03
Hi guys/gals

My PC has 2 hard disks, HDA is windoze and HDB is linux/ubuntu 6.06

Over the christmas break decided to reload windoze. That actually went surprisingly well, lost no documents and now have a relatively nice windows system (mainly for the wife's benefit!)

In doing so i have lost my GRUB boot loader. Turn the puter on and straight into windows it goes. NOT what i want or need!

I have looked at all the ideas for recovering the grub but none of them work. Using an old ubie 5.04 live cd, i can't get grub to initialize. I tried the supergrub cd, but no that didn't either. I just can't get ubie to boot!

Using my slax live cd i can see as clear as day the files that i want to make sure i don't lose by moving/copying to my flashdrive but they do not appear to want to move. Do i need to do something clever to allow me to copy/move? Can anyone recommend a better 'rescue cd'?


I can also  see the grub folder under boot complete with stage1 and stage2 and menu list

I am keen to do this as my next plan is to use the 6.06 install disk to do a partial install up to the point where grub is installed and then escape out, without losing any of my docs/fotos.

Does any one know if it is possible to access the ubie drive thru windows? It would make life very much easier.

I am by the way not very technical so if anyone has any answers please make them cretin proof!

thanks... Simon

---

### Post by Malac on 2007-01-03
You may already have done this but have you tried setting hd1 (second hard drive)  to first boot device in the BIOS and/or bootable/active with fdisk.
As XP will reset which drive is the first boot device this may be your problem and GRUB is still there.

To access ext2 filesystems from Windoze I use "Ext2IFS" but I can't remember where I downloaded it from (sorry) but a Google search for "Ext2IFS_1_10b.exe" should find it.

Hope this helps.

---

