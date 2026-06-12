---
title: "partition error can't boot help!!"
date: 2007-04-05
forum: General Help
---

### Post by ajmorris on 2007-04-05
Something has mucked up my partition table. When i try to boot through grub i get a grub error 17.
Then i boot into Knoppix live c.d, and i can't mount it because it says i need to specify what filesystem it is. So i type ```
sudo mount -t reiserfs /dev/hda6 /mnt/hda6
``` but get the error of ```
mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
fdisk /dev/hda6
```

gets this error : ```
Unable to open /dev/hda

```

any other things i can try? Anyway i can repair this? please help, i have nothing backed up and since i can't mount it i can't get anything off it.

---

### Post by cantormath on 2007-04-05
are you running a reiserfs file system on the drive you are trying to mount?

and this is my 900th post......whoohoo....

---

### Post by ajmorris on 2007-04-05
> **cantormath said:**
> are you running a reiserfs file system on the drive you are trying to mount?

and this is my 900th post......whoohoo....

Yes i am running ReiserFS

---

### Post by ajmorris on 2007-04-05
also fdisk -l  gives this
Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        3648    29302528+   5  Extended
/dev/hda5               1         102      819252   82  Linux swap / Solaris
/dev/hda6   *        1951        3648    13639184+  bb  Boot Wizard hidden

/dev/hda6 is my linux one. Shouldn't it say ReiserFS not Boot Wizard hidden?
can i create a new partition table manually?

I did this again ```
sudo fdisk /dev/hda6
```
this time on the ubuntu live cd instead of the knoppix cd go this error: 

```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 27061.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
```

how do i make a new DOS disklabel?

---

### Post by cantormath on 2007-04-07
if you are trying to mount the partition, have you tried

```

cd /tmp
sudo mkdir folder
sudo mount /dev/hda6 folder
```

or

```
sudo mount -t reiserfs /dev/hda6 folder
```

you need a mount point for the mount of the drive, in this example I am using a folder called folder.

---

### Post by PapaNerd on 2007-04-07
Did you try doing an fsck on that partition?

---

### Post by ajmorris on 2007-04-10
Thanks all for your help. I had tried all those suggestions, i had screwed up my partition. I had to re-install.

---

