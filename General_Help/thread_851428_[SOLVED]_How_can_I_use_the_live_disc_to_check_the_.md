---
title: "[SOLVED] How can I use the live disc to check the hard drive for damage?"
date: 2008-07-06
forum: General Help
---

### Post by curiousnoob on 2008-07-06
After a few days of use on Hardy Heron my parents PC will no longer load either linux or Windows.  When Windows is attempting to load it gives the following:

"A problem has been detected and Windows has been shut down to prevent damage to your computer"
"UNMOUNTABLE_BOOT_VOLUME"
Technical in
***STOP:0X000000ED"0X827D0868'0XC000185'0X00000000 '0X0000000'"

I have read about people getting this when a partition is screwed up but this setup worked for weeks with the machine frequently shut down and turned back on.
For the mean time they are using an Ubuntu Live disc so they can at least get online but I really need to fix this.
Others have suggested it may be the hard drive.  Is there any way to confirm that using tools available in the Live CD?:confused:

---

### Post by drs305 on 2008-07-06
Try the Super Grub Disk - it amy be the boot record that is messed up and this disk can help sort it out.

[Super Grub Disk]("http://www.supergrubdisk.org/")

I'd start trying to restore windows since it's easier to get ubuntu back working afterward than vice versa.

---

### Post by curiousnoob on 2008-07-06
> **drs305 said:**
> Try the Super Grub Disk - it amy be the boot record that is messed up and this disk can help sort it out.

[Super Grub Disk]("http://www.supergrubdisk.org/")

I'd start trying to restore windows since it's easier to get ubuntu back working afterward than vice versa.

That's a good idea.  I'll have to get the program from another PC later.  In the meantime is there any way to make sure the current hard drive is working correctly?

---

### Post by rokytnji on 2008-07-06
Download this and burn as an iso so it will boot from cdrom. Has all kinds of hardrive checking tools.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by curiousnoob on 2008-07-07
> **rokytnji said:**
> Download this and burn as an iso so it will boot from cdrom. Has all kinds of hardrive checking tools.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

This looks very promising.  The programs seem to be for specific brands of Hard Drives, though.  How can I find out the type of HDD I have without opening the case?  
Between all of the different programs is there one that is more popular?

---

### Post by Afkpuz on 2008-07-07
If you want to use an ubuntu live CD, boot from it and goto System>Administration>Partition Editor

That's actually gparted and can change partitions and can check hard drives for errors.  I don't think it can repair your boot problem, but it can fix errors in a drive.

---

### Post by VMC on 2008-07-07
> **curiousnoob said:**
>   How can I find out the type of HDD I have without opening the case?  

Try this(switch sda for your hard drive):
```
 sudo hdparm -i /dev/sda
```

---

### Post by curiousnoob on 2008-07-07
> **Afkpuz said:**
> If you want to use an ubuntu live CD, boot from it and goto System>Administration>Partition Editor

That's actually gparted and can change partitions and can check hard drives for errors.  I don't think it can repair your boot problem, but it can fix errors in a drive.

Thanks, I was able to find out the model using this but I was unable to find an option for checking the disc for errors.  How do I use this for that?

---

### Post by dentaku65 on 2008-07-07
> **curiousnoob said:**
> Thanks, I was able to find out the model using this but I was unable to find an option for checking the disc for errors.  How do I use this for that?

Boot with any live cd (to those kind of things I prefer Knoppix or SystemRescueCD, but Ubuntu is the same); anyway in the Grub of Knoppix type:
```
knoppix 2 lang=xx 
```
(xx is your keyboard region)
Knoppix will start in text mode, then type:
```
fsck -y /dev/sdax
```
(sda**x** is the partition number where your system is installed)

Fsck should fix (if possible) your hd.

---

### Post by curiousnoob on 2008-07-07
> **dentaku65 said:**
> Boot with any live cd (to those kind of things I prefer Knoppix or SystemRescueCD, but Ubuntu is the same); anyway in the Grub of Knoppix type:
```
knoppix 2 lang=xx 
```
(xx is your keyboard region)
Knoppix will start in text mode, then type:
```
fsck -y /dev/sdax
```
(sda**x** is the partition number where your system is installed)

Fsck should fix (if possible) your hd.

Any way to do this with the Hardy Heron Live disc?  I won't have access to another PC with a burner for another day or so.

---

### Post by curiousnoob on 2008-07-07
Let me clarify my last post.  What I meant to say is if I am using Hardy Heron how do I do anything in Grub?  Do you mean the Terminal?  When in Grub I thought you could only choose the OS you wanted to load.

---

### Post by dentaku65 on 2008-07-07
> **curiousnoob said:**
> Let me clarify my last post.  What I meant to say is if I am using Hardy Heron how do I do anything in Grub?  Do you mean the Terminal?  When in Grub I thought you could only choose the OS you wanted to load.

With Hardy live cd load it then when you are inside Gnome open a terminal window and do:
```
fsck -y /dev/sdax
```
x is the number of partition where your Ubuntu is installed on hard disk

---

### Post by curiousnoob on 2008-07-09
> **dentaku65 said:**
> With Hardy live cd load it then when you are inside Gnome open a terminal window and do:
```
fsck -y /dev/sdax
```
x is the number of partition where your Ubuntu is installed on hard disk

Thank you, that solved my problem completely.  I can now get into linux and I now know there is a system file missing for Windows which prevents it from loading.

---

