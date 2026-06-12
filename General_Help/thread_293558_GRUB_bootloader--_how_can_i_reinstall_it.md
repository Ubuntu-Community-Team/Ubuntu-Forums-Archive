---
title: "GRUB bootloader-- how can i reinstall it?"
date: 2006-11-05
forum: General Help
---

### Post by Beowulf.1000 on 2006-11-05
If Windows XP is reinstalled (system trashed from virus), the Ubuntu linux bootloader (Grub) is lost, so how can the linux bootloader be reinstalled after a reinstall of WindowsXP?  I used to use Mandriva linux and its install CD had a rescue mode with an option to automagically reinstall the LILO bootloader; I can not find such an easy option on the Ubuntu CD.  

Windows is in C: (hda), Ubuntu on D: (hdb). Ubuntu 6.06.

---

### Post by Ramses de Norre on 2006-11-05
Boot the live cd and do this in terminal:
```
sudo grub
root (hd0,1)
setup (hd0)
quit
sudo update-grub
sudo reboot
```

The hd0,1 assumes ubuntu is in the second partition of your first hard disk, you need to change it to the appropriate values (it starts counting from zero!).
hd0 is the mbr where you probably wants to install grub into.

---

### Post by Beowulf.1000 on 2006-11-05
Ubuntu is not on the first hard disk, ubuntu is on a second (dedicated to linux) hard disk. So I am guessing
  root (hd0,1)
should be changed to
  root (hd1,0)
but that 
  setup (hd0)
would remain as is-- I am guessing that the setup() function is telling grub where to put the bootloader?

I am really not well versed in grub at all, I have always used LILO. I will have to study up on grub to become more comfortable with it.

---

### Post by Enforcer83 on 2006-11-05
Ok i am having the same issue.  I run fdisk and this is the output.

```
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612        5161    20482875    f  W95 Ext'd (LBA)
/dev/hda3            5162        9729    36692460    7  HPFS/NTFS
/dev/hda4            9730       24792   120993516    7  HPFS/NTFS
/dev/hda5   *        2612        5053    19615333+  83  Linux
/dev/hda6            5054        5161      867478+  82  Linux swap / Solaris

```

I assume that i should run this code to setup grub correctly.

```
sudo grub
root (hd0,4)
setup (hd0)
quit
sudo update-grub
sudo reboot
```

Is this correct?

---

### Post by orb9220 on 2006-11-05
>  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612        5161    20482875    f  W95 Ext'd (LBA)
/dev/hda3            5162        9729    36692460    7  HPFS/NTFS
/dev/hda4            9730       24792   120993516    7  HPFS/NTFS
/dev/hda5   *        2612        5053    19615333+  83  Linux
/dev/hda6            5054        5161      867478+  82  Linux swap / Solaris

All show as hda which is one hardrive. Are you sure you have 2 hardrives or partitions. If all the partitions are on one hd then
It would be hd0,0

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by Ramses de Norre on 2006-11-05
@orb9220: hda is one harddisk but it has six partitions so he'll need hd0,4 which is hda5 and seems to contain the only linux filesystem.

@Enforcer83: Yes, you've got the right one.

@Beowulf.1000: Yes that should do.

---

### Post by Enforcer83 on 2006-11-05
Thanks Ramses de Norre everything works now

---

### Post by TheGreenMutt on 2006-11-16
i have the same problem but i don't know exacty what partition linux is one or wich one is windows i put in the live disk start the comp up and it runs the ubuntu installer all i see for input is    "boot: "  i enter fdisk and its says something to the tune of boot not found or some thing like that any idea of what to do to find out what partition i have what on

---

### Post by Ramses de Norre on 2006-11-16
You need to start the live session, not the installer. Live sessions are on the desktop cd for dapper or edgy and on separate discs for older versions.

---

### Post by TheGreenMutt on 2006-11-16
thx apperently i have an install cd not a live cd so i check ubuntu.com for a live cd download and all the mirrors were down can some one post a link to ones that work please

---

