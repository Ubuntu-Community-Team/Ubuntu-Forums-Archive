---
title: "GRUB wont install?"
date: 2008-01-06
forum: General Help
---

### Post by 2Dum2Kno on 2008-01-06
i have a question, im having problems with grub its not installing on UBUNTU 7.10
may i ask why?

also, if the solution is super grub, how do i boot it? i konw how to use iso:lolflag:

---

### Post by logos34 on 2008-01-06
Can you describe your situation in more detail?

You have to download the supergrub iso, then burn it to a CD **as an image**.  Then boot form it like you would any install cd

---

### Post by 2Dum2Kno on 2008-01-06
well is whats going on, ia that i install the OS in my partitiond part of the HD (:/U) andwhen i install i come to an error saying that GRUB faital error can not install.... where exactly am i suppost to place the file? in (hd0)... please let me know

___________
2Dum2Kno
Now Relaxed, no longer mad at my Vista Computer :lolflag:

---

### Post by logos34 on 2008-01-07
(hd0) is the default location--puts grub on the mbr (master boot record).  Normally that's fine.  You have only one hard disk in system, right?  I'd check the Bios settings...make sure hard disk is in correct mode (LBA, Auto).  Or maybe the mbr has[ write-protection]("http://users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect") enabled.  Could be any number of things.  

Do you have a floppy drive?  If so you could tell it to write grub to floppy.  This would be a good temporary solution until you figure out what;s going on.  Just replace (hd0) with **(fd0)**

---

### Post by 2Dum2Kno on 2008-01-07
ok thaks ill try that i dont have a floppy tho

the super grub desent work, it says not found, i burned the ISO correctly!
so i need to turn off MBRP, ill try that

:KS Thanks il try iy out and report back within the next 1hour

---

### Post by 2Dum2Kno on 2008-01-07
i cant find the mbr settings looked in vista and bios i cant find it :(

---

### Post by logos34 on 2008-01-07
not sure what the problem is burning the SGD iso to cd...

Since you're trying to dual boot ubuntu with vista (or is vista on another machine?), I'd try [EasyBCD]("http://neosmart.net/wiki/display/EBCD/linux") next.  So you'll use Vista boot manager instead of Grub to boot ubuntu.

---

### Post by 2Dum2Kno on 2008-01-07
ok ive installed EasyBSD
but under add or remove enteries what do  i do

---

### Post by Computer Guru on 2008-01-07
If you don't already have GRUB installed *anywhere* then use NeoGrub and create a configuration file to boot into Ubuntu [as shown here]("http://neosmart.net/wiki/display/EBCD/NeoGrub+Linux").
If you have GRUB installed to the bootsector, then just add a normal GRUB entry in EasyBCD selecting the right partition.
If GRUB is installed to the MBR, continue on with the [Ubuntu pictorial]("http://neosmart.net/wiki/display/EBCD/Ubuntu").

---

### Post by 2Dum2Kno on 2008-01-07
> **Computer Guru said:**
> If you don't already have GRUB installed *anywhere* then use NeoGrub and create a configuration file to boot into Ubuntu [as shown here]("http://neosmart.net/wiki/display/EBCD/NeoGrub+Linux").
If you have GRUB installed to the bootsector, then just add a normal GRUB entry in EasyBCD selecting the right partition.
If GRUB is installed to the MBR, continue on with the [Ubuntu pictorial]("http://neosmart.net/wiki/display/EBCD/Ubuntu").

What happens if it brings up a grub menu at the beginning? when u load the Vista BootLoader?

```

# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries

title Ubuntu
find --set-root /boot/vmlinuz-2.6.17-10-generic
kernel /boot/vmlinuz-2.6.17-10-generic ro root=/dev/sda4
initrd /boot/initrd.img-2.6.17-10-generic

```
what do i change this to?

---

### Post by logos34 on 2008-01-07
[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)
(--> 'Ceate the Linux boot option in Vista')

remember: for it to work you have to install grub to bootsector of ubuntu root partition (using ubuntu live cd)

---

### Post by Computer Guru on 2008-01-07
> **2Dum2Kno said:**
> What happens if it brings up a grub menu at the beginning? when u load the Vista BootLoader?

EasyBCD -> Bootloader Management -> Reinstall Vista Bootloader

---

### Post by 2Dum2Kno on 2008-01-07
read the post that i edited... its not loading eather way :( i must be dum or sumthing, cananyone come on msn and do remote asstance?

---

### Post by 2Dum2Kno on 2008-01-07
also another problem... i just noticed that when i click ubuntu in the main menu of bootloader it says cant be found

---

