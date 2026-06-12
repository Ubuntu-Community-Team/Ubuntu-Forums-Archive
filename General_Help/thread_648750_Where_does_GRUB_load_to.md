---
title: "Where does GRUB load to?"
date: 2007-12-24
forum: General Help
---

### Post by pilot550 on 2007-12-24
I normally run Vista and Ubuntu on my laptop. But recently I decided to try Mythbuntu. I junked up my Vista partition pretty good so I decided to start from scratch. I deleted the Linux partitions and reloaded my Vista image. To my surprise GRUB came up at boot. I then booted from my Vista DVD to "repair" the Master Boot Record. But once again, GRUB came up.

Obviously GRUB was not on my Linux partition. There is a hidden partition at the beginning of my drive from the manufacturer for restoring the laptop. Could it be there? Or is there some sort of lower level boot record on my Vista partition that would not have been overwritten by my (Norton Ghost 2003) Image.

I have already partitioned my drive and loaded Ubuntu, and everything is working, so it's not a big deal I'm just curious.

---

### Post by Existentialist on 2007-12-24
It is installed to the drives MBR (master boot record).  Wikipedia has a good amount of information on MBRs.

[http://en.wikipedia.org/wiki/Mbr](http://en.wikipedia.org/wiki/Mbr)

---

### Post by burbankmarc on 2007-12-24
That is a good question. And you may be right when you say it's installed to the first 'factory' partition.

open up a terminal and do the following:

```
sudo fdisk /dev/*yourHDD*
```

then type 'p'

and you should get something that looks like this:

```
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32          93      498015   82  Linux swap / Solaris
/dev/sda3              94         701     4883760   83  Linux

```

all the partitions with a * are bootable. So if your 'factory' partition is bootable then it's there's a good chance that it is on that partition.

to toggle the boot flag simply type:

```
Command (m for help): a
Partition number (1-6): 1

```

FYI if you jack up your partitions and don't want to save the changes just type q, but if you're content with said changes simply type w for write.

---

### Post by pilot550 on 2007-12-24
I guess It's not on the factory restore partition because it shows my Vista partition as active:

```
Command (m for help): p

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2ad5a3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         765     6144831   27  Unknown
/dev/sda2   *         766       23046   178972132+   7  HPFS/NTFS
/dev/sda3           23047       24261     9759487+  83  Linux
/dev/sda4           24262       24321      481950    5  Extended
/dev/sda5           24262       24321      481918+  82  Linux swap / Solaris

```

I read through the Master Boot Record WIKI. So the MBR is on the beginning of sda, the drive itself not any specific partition. By loading a Ghost image file on to a specific partition I am not changing the MBR, just what is on that partition, which could "break" it from booting. The MBR then runs the Volume Boot Record which contains GRUB. So if I select a deleted partition I obviously get an error message. But when I tell my Vista install DVD to "repair" the MBR it fixes the instructions contained in the VBR holding GRUB to properly boot Vista.

Does that sound right? It's about as much sense as I can make of it.

---

### Post by louieb on 2007-12-24
Without going into all the detail. The GRUB program is named stage2 and most distros put it in the /boot/grub folder. 
The code in the MBR is just a pointer to some boot loader such as GRUB or NTLDR (windows). 
For a lot more detail check out the Dual Boot link in my signature. Rock on.

---

### Post by Ocxic on 2007-12-24
you don't want to use the windows disk to "repair" your drive as that would get rid of grub, and you would be unable to boot ubuntu. untill you setup the windows boot loader to boot ubuntu. why don't you want grub anyways?

---

### Post by pilot550 on 2007-12-24
I actually do want GRUB. I have my system dual booting again with everything running perfectly. I just didn't understand how GRUB could still be there after and Image re-load and a Vista MBR repair. It makes a lot more sense now. Thanks for all the info guys.

---

