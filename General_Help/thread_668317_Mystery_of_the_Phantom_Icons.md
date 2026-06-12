---
title: "Mystery of the Phantom Icons?"
date: 2008-01-15
forum: General Help
---

### Post by stropyboy11 on 2008-01-15
I am having a rather odd problem. When I first installed ubuntu, both my Windows and Ubuntu hard drive partitions showed up as icons on my desktop. Now, neither icon will show up, which is really annoying considering there's no other way I've found to browse my Windows partition (helpful when looking for Word documents I did in school). Does anyone have any idea?

-Stropko

---

### Post by SOULRiDER on 2008-01-15
Do they still appear in the places menu? If they dont its ebcause theya re not being mounted, dont worry, mounting them manually is a piece of cake.

---

### Post by stropyboy11 on 2008-01-15
No they're not :(

Any ideas now?

---

### Post by SOULRiDER on 2008-01-15
Could you please paste the output of this command:
```
sudo fdisk -l
```

Please, remember to use the **[CODE]** tags.

---

### Post by stropyboy11 on 2008-01-15
[Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13882b5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12162    97687216+   7  HPFS/NTFS
/dev/sda2           12162       12423     2096128+   f  W95 Ext'd (LBA)
/dev/sda3           12423       13728    10484736   83  Linux
/dev/sda4           13729       14593     6948112+   7  HPFS/NTFS
/dev/sda5           12162       12423     2096128   82  Linux swap / Solaris]

---

### Post by SOULRiDER on 2008-01-16
Im guessing the one you need is /dev/sda4 so lets do this

First of all install the ntfs-3g drivers so you can write tot he drive (im not sure if they are installer or not by default so installing them manually wont hurt)
```
sudo aptitude install ntfs-3g
```
Now lets create a mountpoint, I will make it /media/sda4, but you could make it /media/windows or something else you want
```
sudo mkdir /media/sda4
```
Now lets edit fstab acordingly, press alt + f2 and type
```
gksu gedit /etc/fstab
```
And at the end add this (if you chose another mountpoint modify the /media/sda4 part):
```
/dev/sda4 /media/sda4 ntfs-3g rw,auto,user,exec 0 0
```
Then reboot and an icon should appear either in the desktop or in the places menu. If it doesnt go to /media/sda4 (or whatever your mountpoint was) and your files should be there.

For more info on fstab check thsi site out: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Good luck and post results, if its solved please mark the thread as solved.

---

