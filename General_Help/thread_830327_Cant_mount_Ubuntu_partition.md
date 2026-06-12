---
title: "Cant mount Ubuntu partition"
date: 2008-06-15
forum: General Help
---

### Post by screaminfakah on 2008-06-15
Hello,
I tried to install Ubuntu Studio on new partition and the install failed due to some corrupt files.
It screwed up my MBR and Grub had an error. I loaded my install cd and got online and fixed Grub.
When I tried to select Hardy from the grub list it said it could not mount and gave me an error code 17. Vista still was able to boot though (thank goodness).

Any ideas if Hardy is trashed or is there a possible fix?

Thanks

---

### Post by VMC on 2008-06-15
> **screaminfakah said:**
> Hello,
I tried to install Ubuntu Studio on new partition and the install failed due to some corrupt files.
It screwed up my MBR and Grub had an error. I loaded my install cd and got online and fixed Grub.
When I tried to select Hardy from the grub list it said it could not mount and gave me an error code 17. Vista still was able to boot though (thank goodness).

Any ideas if Hardy is trashed or is there a possible fix?

Thanks

We need to see a few outputs:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by screaminfakah on 2008-06-15
Here is what it displayed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       31055   239215882+   6  FAT16
/dev/sda3           31056       41414    83208667+   7  HPFS/NTFS
/dev/sda4           41415       60801   155726077+   5  Extended
/dev/sda5           60083       60801     5775336   82  Linux swap / Solaris
/dev/sda6   *       51507       59727    66035151   83  Linux
/dev/sda7           59728       60082     2851506   82  Linux swap / Solaris
/dev/sda8           41415       51088    77706342   83  Linux
/dev/sda9           51089       51506     3357553+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by screaminfakah on 2008-06-15
Nevermind,  Im just going to dump the sh#! and reinstall.  I backed up everything to disc so I wont loose much in the long run.

Later

---

### Post by meierfra. on 2008-06-15
(Edit: it seems I came a minute to late)

At the grub menu at boot up, select Ubuntu, but do not press enter.Press "e" instead. At the new screen press "e" again. You get a line which looks like

root (hd0,?)

Change it do

root (hd0,5)

So change the second number to 5, but do not change anything else.
Press "enter" and then "b" to boot.

This should boot you into ubuntu. (if not, try 7 in place of 5)
 Once you booted into Ubuntu, you still need to make this change permanent:

Open a terminal and type


```
gksudo gedit /boot/grub/menu.lst
```

(l is a lowercase L)

change

# groot=(hd0,?)

to

# groot=(hd0,5)

(of course use "7", if "5" did not work earlier)

Save the file. Then in the terminal:

```
sudo update-grub
```

---

