---
title: "Corrupted/removed Grub, can't boot into Linux. Partition not visible from Gparted."
date: 2021-01-28
forum: General Help
---

### Post by SirTheSurfer on 2021-01-28
To make long story short yesterday I typed some commands that resulted in me being unable to boot into my system. I think that grub might have been removed/corrupted. Below I provided output of some commands I managed to run while in Liveusb environment.
 -while running Gparted the only partition I can see is /dev/sda1 which is the pendrive itself. 
-My old partition is visible from UEFI bios

fdisk -l-u

```
Disk /dev/loop0: 1.98 GiB, 2103640064 bytes, 4108672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 3.77 GiB, 4027580416 bytes, 7866368 sectors
Disk model: USB DISK        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x025ee74f

Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *     2048 7866367 7864320  3.8G  c W95 FAT32 (LBA)

```


cat /proc/partitions

```
major minor  #blocks  name

   7        0    2054336 loop0
   7        1      30600 loop1
   7        2      56276 loop2
   7        3     261700 loop3
   7        4      63580 loop4
   7        5      50980 loop5
   8        0    3933184 sda
   8        1    3932160 sda1
```

I know for a fact that **sda **is the partition with my old linux installation. I think that it's worth to notice that it is visible through cat/proc/partitions but not through fdisk -l -u
          sudo fsck /dev/**sda**:

```

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda is in use.
e2fsck: Cannot continue, aborting.
```

Here is the log from boot-repair. I might add there was visible only button for creating logs. No option for quick fix.
[URL="https://paste.ubuntu.com/p/sg3yPGFBrJ/"]https://paste.ubuntu.com/p/sg3yPGFBrJ/

[/URL]
Also, I am greeted by following message by installation wizard when attempting reinstall:

```

This computer uses Intel RST (Rapid Storage Technology). You need to turn off RST before installing Ubuntu. For instructions, open this page on a phone or other device: help.ubuntu.com/rst
```

I did disable this option in Bios however the error didn't go away.



Thoughts?

---

### Post by ajgreeny on 2021-01-28
Removal of grub from the system should not stop gparted or the live system from still seeing the hard disk.

When running the live USB do any volumes show in the left hand pane of the file-manager?  That would normally show any partitions on the hard disk, and clicking on them would normally mount them so you can see what they contain.

If you can see any files at all on the root partition of the installed system, though it does seem unlikely if gparted and fdisk do not see anything, you might be able to see what command you used in your .bash_history file (in what was your home.  The command you used may give us more chance of figuring out what you did, therefore hopefully giving us more chance to help you solve this.

Does the hard disk show in your BIOS/UEFI settings page?

You say "I know for a fact that sda is the partition with my old linux installation." but sda is the disk not a partition on it; that would be sda1 or sda2, etc etc.

---

### Post by SirTheSurfer on 2021-01-28
Hi!

> **ajgreeny said:**
> 
When running the live USB do any volumes show in the left hand pane of the file-manager?  That would normally show any partitions on the hard disk, and clicking on them would normally mount them so you can see what they contain.

If you can see any files at all on the root partition of the installed system, though it does seem unlikely if gparted and fdisk do not see anything, you might be able to see what command you used in your .bash_history file (in what was your home.  The command you used may give us more chance of figuring out what you did, therefore hopefully giving us more chance to help you solve this.

No luck getting there through liveusb but I did manage to open it using grub cmd, below few last commands: 

```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install update-notifier-common
cd /var/lib/dkpkg
sudo mv info info.bak
sudo mkdir info
sudo apt-get upgrade
sudo apt-get install linux-tools-common
```

I wish I could paste the whole file here with all of the commands from yesterday but I don't know how to go about this in Grub cmd.

> **ajgreeny said:**
> 
Does the hard disk show in your BIOS/UEFI settings page?
You say "I know for a fact that sda is the partition with my old linux  installation." but sda is the disk not a partition on it; that would be  sda1 or sda2, etc etc.


Yes. Oh well, good to know!

---

### Post by SirTheSurfer on 2021-01-28
SOLVED

Turns out the setting I thougt to be RST wasn't RST after all...so after turing off the RST I managed to repair it with boot-repair.

---

