---
title: "Grub Boot Error 17 Major Help"
date: 2008-05-11
forum: General Help
---

### Post by Drewmanfuu on 2008-05-11
A while ago I accidently deleted a partition on my Hard drive causing Grub Boot Error 17 and Ive been extremely frustrated with trying to fix it and any help would be greatly appreciated. Im using a Life Book P1120 laptop that has no CD drive, making things difficult. I tried using a USB Cd Drive but no matter what the Bios settings it never recognized the drive. I tried a USB flash drive with a version of linux but the bios is to old and it wont support booting from USB Flash Drive. Then tried reinstalling windows with floppy disks with a USB Floppy Drive to only get an error screen at the end of the installation causing the installation to do nothing leaving me right back where I started. I really don't want this laptop to go to waste its compact and works fine(when it was working. Please if any one could help I'd really appreciate it.

---

### Post by Drewmanfuu on 2008-05-11
anyone?? please?

---

### Post by zvacet on 2008-05-12
Look if you can fet any help from [here.]("http://users.bigpond.net.au/hermanzone/p15.htm#17")And,If I may ask you,which partition you deleted?

---

### Post by Sef on 2008-05-12
1) Do not bump your thread unless 24 hours have gone by.  Otherwise you could end up with an infraction.

2) This is GRUB error 17:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB

Let's do this to check your partitions:

Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` Small L

Paste the results here.

---

### Post by Drewmanfuu on 2008-05-12
Sorry for bumping I just got a lil anxious.
and as for" Applications > Accessories > Terminal" I cant access any of my operating systems on the hard drive so how do I go about doing this.

---

### Post by confused57 on 2008-05-12
> **Drewmanfuu said:**
> Sorry for bumping I just got a lil anxious.
and as for" Applications > Accessories > Terminal" I cant access any of my operating systems on the hard drive so how do I go about doing this.
If you're getting a grub boot menu, you can try highlighting your first Ubuntu entry, press "e", select the line with root, press "e" again, then try changing root from (hd0,x) to (hd0,0), (hd0,1), (hd0,2), etc...a good bet would be to reduce the partiton by one(e.g. hd0,2 to hd0,1)...press "enter", then "b" to boot.  You may need to try several different options for the root partition.

---

### Post by dizee on 2008-05-13
> **Drewmanfuu said:**
> Sorry for bumping I just got a lil anxious.
and as for" Applications > Accessories > Terminal" I cant access any of my operating systems on the hard drive so how do I go about doing this.
Boot from the live cd.

---

### Post by Drewmanfuu on 2008-05-13
I appreciate the help but keep in mind one thing, the computer turns on and goes directly to the boot error, no menu no nothing. Also as I said before the computer is not recognizing the CD-Rom drive I have, Ill look into getting a new one but in the mean time I can only boot from floppies.

---

### Post by vancouverite on 2008-05-13
Maybe have a look at these to make a bootable grub floppy.

<http://ubuntuforums.org/archive/index.php/t-6195.html>
or
<http://gentoo-wiki.com/TIP_Bootable_Floppy_with_GRUB>

---

### Post by coffee_bean on 2008-06-16
> **Drewmanfuu said:**
> I appreciate the help but keep in mind one thing, the computer turns on and goes directly to the boot error, no menu no nothing. Also as I said before the computer is not recognizing the CD-Rom drive I have, Ill look into getting a new one but in the mean time I can only boot from floppies.
Then it sounds like you'll need to change your bios settings, putting your CD-ROM before the hard disk in the boot discovery order.

---

### Post by GenesisV2.0 on 2008-06-16
I know its a bit of a long winded way of doing things but seen as your laptop/computer is inoperable i would do a live install using a parralel cable connected to a working pc with a cd drive.

Then basically you have the option of live booting and fixing your hard drive from the live OS or just installing a new os via a parralel network connection.

Parralel cables off ebay are relatively cheap and you must have a freind with a computer that you can borrow for 15 mins while you chuck a live cd in and do a serial boot. 

just giving my opinion
(virgin post)

---

