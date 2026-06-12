---
title: "Ubuntu won't mount USB hard drive or memory cards."
date: 2007-12-15
forum: General Help
---

### Post by Ghostlove on 2007-12-15
Everything was working perfectly last week. Then I did something which screwed everything up, so  I decided to do a fresh install. (My first install was done from a Gutsy download from the site, the fresh install was done from the 'official' Gutsy CD. Not sure if that means anything).

Since the fresh install, everything seems to be going tits-up.

First problem:

When I first rebooted after the fresh install, my external hard drive was just automatically recognised and mounted, and I could access, change and delete whatever I wanted. Then I had to reboot and now... it doesn't do anything. When I try to manually mount it, I get the following message:

```
mount: special device /dev/sdc1 does not exist
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

Second problem:

My box has a built-in card reader. Before the fresh Gutsy install, all I had to do was put my SD card into the relevant slot, and it appeared on my desktop ready to move my photographs from. Now, nothing happens at all.

I downloaded pysdm (Storage Device Manager) which at least allows me to see what's on the SD card (and a Sony Memory Stick Duo on an adapter for that matter) but it's really, really frustrating to use as I don't have read/write access on either card, so I have to use sudo rm/mv/cp to delete, move or copy any files. Previously, when Ubuntu automatically recognised the memory cards, I could do whatever I wanted on them.

So... does anyone know why Gutsy has decided to randomly hate my external hard drive? And can anyone shed some light on why my memory cards no longer work? I'm almost tempted to go back to good ol' Feisty... everything worked perfectly there. :confused:

---

### Post by logos34 on 2007-12-15
what does

**sudo fdisk -l** (lowercase L)
 
show?

---

### Post by Ghostlove on 2007-12-15
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6decfe49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         984     1983619+   6  FAT16
```

Now that is just stupidly weird... I KNOW that hard drive is ntfs. It always has been!

---

### Post by logos34 on 2007-12-15
hmm...you could always back up whatever is on it and reformat as ntfs using gparted.  But it will only be read-only unless you mount it with ntfs-3g.

---

### Post by Ghostlove on 2007-12-15
But... I can't back up what's on it, because I can't access it!

---

### Post by logos34 on 2007-12-15
> **Ghostlove said:**
> But... I can't back up what's on it, because I can't access it!

what about 

sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1

can you access it now?

---

