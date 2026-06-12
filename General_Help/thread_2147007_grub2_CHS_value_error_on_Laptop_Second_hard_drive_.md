---
title: "grub2 C/H/S value error on Laptop Second hard drive (ODD)"
date: 2013-05-20
forum: General Help
---

### Post by AnotherNoob on 2013-05-20
[SIZE=4][COLOR=#333333][FONT=Ubuntu Beta]I was living happily with my one hard drive in laptop then I installed a SSD as my first (hd0) then installed the old drive in laptop's second hard drive caddy in CD/DVD drive bay.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]now I can't boot in my old drive OS, I am getting C/H/S values error, in bios there are no options for second hard drive (Dell Inspiron N5010, bios version A15)[/FONT][/COLOR]
[/SIZE][COLOR=#333333][FONT=Ubuntu Beta][SIZE=4]I know very little about grub so here's some outputs.[/SIZE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta][SIZE=3][grub.cfg]("http://paste.ubuntu.com/5676372/")[/SIZE]
[/FONT][/COLOR]
[SIZE=3][COLOR=#333333][FONT=Ubuntu Beta][fdisk -l]("http://paste.ubuntu.com/5676376/")
[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#333333][FONT=Ubuntu Beta][blkid]("http://paste.ubuntu.com/5676373/")

hope to get some help here same question asked at [/FONT][/COLOR][/SIZE][http://askubuntu.com/questions/296995/grub2-c-h-s-value-error-on-laptop-second-hard-drive-odd](http://askubuntu.com/questions/296995/grub2-c-h-s-value-error-on-laptop-second-hard-drive-odd)

---

### Post by oldfred on 2013-05-20
Drives have not actually used CHS values for about 15 years when hard drives went over 8GB. But some laptops will not boot a second drive in a caddy where DVD was.

What setting for drives do you have? Generally you have have something like LBA, Large, IDE, RAID, possibly the newer AHCI. Now AHCI is preferred or at least large or LBA which is just large block allocation. You should not have RAID nor IDE.

---

### Post by AnotherNoob on 2013-05-20
in bios Sata mode is AHCI enabled, there's also second option ATA.

---

### Post by oldfred on 2013-05-20
If in AHCI then does not BIOS show second hard drive as a boot choice. If not theny BIOS will not let you boot it directly.

You might check and see if they have an update to BIOS.

---

### Post by AnotherNoob on 2013-05-20
no bois don't let me boot into second hard drive in any way and i am using latest version of bios which is A15.

---

### Post by AnotherNoob on 2013-05-21
now can we do something ?

---

### Post by oldfred on 2013-05-21
Normally you use this to boot a flash drive that BIOS does not support by using CD to boot plop & then plop can load flash drive.

If you can boot from a flash drive you may be able to install plop to flash drive to boot your second drive. 

 Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

