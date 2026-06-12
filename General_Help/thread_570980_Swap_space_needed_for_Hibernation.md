---
title: "Swap space needed for Hibernation?"
date: 2007-10-08
forum: General Help
---

### Post by Havek on 2007-10-08
I just recently installed Ubuntu on my Hp laptop.  So now it has both Xp and Fiesty Fawn.  I did not make a swap partition when i installed and now when i try to put my laptop into hibernation in Ubuntu it says there is no swap space and just goes to the login screen.  Do i have to create a swap partition?

---

### Post by Pumalite on 2007-10-08
For hybernation: /swap at least=RAM

---

### Post by Havek on 2007-10-08
> **Pumalite said:**
> For hybernation: /swap at least=RAM

So i need to create another partition thats 1 gig( i have 1 gig of ram), so how do i go about doing that with out messing up my windows?

---

### Post by Pumalite on 2007-10-08
Post:
sudo fdisk -lu

From the output I can help you.

---

### Post by Havek on 2007-10-08
Here is the output
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   178915904    89457921    7  HPFS/NTFS
/dev/sda2       194948775   195366464      208845   88  Linux plaintext
/dev/sda3       178915905   194161589     7622842+  83  Linux
/dev/sda4       194161590   194948774      393592+   5  Extended
/dev/sda5       194161653   194948774      393561   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Pumalite on 2007-10-08
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, right click sda5 and in the menu, choose 'resize partition'

---

### Post by Havek on 2007-10-08
> **Pumalite said:**
> Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, right click sda5 and in the menu, choose 'resize partition'

Wait so i do have a swap partion it just is not large enough and i just have to resize it?  Ok that sounds pretty easy and i am pretty sure i can do it.  Thanks a lot for your help.

---

