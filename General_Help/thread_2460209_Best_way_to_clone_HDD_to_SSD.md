---
title: "Best way to clone HDD to SSD?"
date: 2021-04-05
forum: General Help
---

### Post by techmasterdesign on 2021-04-05
Hey everyone. I'll start with my system information. 


OS: Linux
Distro: Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-70-generic x86_64)
Current HDD: 1TB, with 30GB populated
Target SSD: Micron MTFDDAV480TDS-1AW1ZABYY 5300 PRO 480GB,SATA, M.2, 22x80mm,3D TLC,1.5DWPD
Adapter: Dell BOSS-S1 Boot Optimized Server Storage Controller Card 2 x M.2 SSD (72WKY)
Server: Dell Poweredge 240
Contents of /sys/firmware folder: acpi, dmi, memmap
Livepatch: enabled
Boot type: BIOS, verified by the fact that the "/sys/firmware/efi" folder doesn't exist
Partion table of current HDD: GPT


What i'm trying to do is basically clone my entire system from the HDD to the new SSD.
I've heard of using GParted, Clonezilla, Timeshift, etc. or even doing a clean install and then replacing all the changed files/folders in the OS (I don't want to do that). 
I also heard that the dd command only works if the target drive is the same size or larger than the current drive. 
What do you guys recommend as the best/easiest way to clone the entire system, and what settings will I have to change in the BIOS for the NVME SSD (boot settings, other settings).

Thanks for your help in advance.

---

### Post by tea for one on 2021-04-05
Please post the details (within code tags) of your existing partitions.
```
sudo parted -l
```

---

### Post by techmasterdesign on 2021-04-05
[COLOR=#000000][FONT=Menlo]No problem, here is the output of **sudo parted -l:**

Model: ATA ST1000NM0018-2F2 (scsi)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk /dev/sda: 1000GB[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Partition Table: gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
Disk Flags: [/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]Number  Start   End     Size    File system  Name  Flags[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 1      1049kB  2097kB  1049kB                     bios_grub[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] 2      2097kB  1000GB  1000GB  ext4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by tea for one on 2021-04-05
I have noticed that you are not using UEFI mode because you do not have an ESP.
You may want to think about a fresh install in UEFI mode.

Anyway, assuming that your 30GB of data is on partition sda2, I would consider:-

Boot into a live Ubuntu session
Take a **back-up**
Use gparted to reduce sda2 to, for example, 450GB
Test your reduced size original OS to satisfy yourself that the partition reduction has not created a problem

If everything is OK
Create two identical size (or larger) partitions on your target disk (using a live session)
i.e. sda1 minimum 1049kB and sda2 minimum 450GB

Then use Clonezilla [https://clonezilla.org/](https://clonezilla.org/) with the option [COLOR="#0000FF"]Device to Device using Partitions[/COLOR]
Two operations required because you have two partitions.

Thoroughly test your new SSD before re-using the 1TB HDD

---

### Post by techmasterdesign on 2021-04-05
Thanks for the clear instructions. Will try this and let you know how it goes.

---

### Post by techmasterdesign on 2021-04-06
I have reduced the size of sda2 with no problems. Absolutely amazing! The size of the NVME SSD is listed as 480GB but was actually 447GB so I shrunk to 446GB to leave 1GB (more than enough) for the boot partition. Weird issue arrose after using gparted with ubuntu live. When I tried to boot back into ubuntu live after testing that no problems arrose on the HDD fter shrinking, by selecting a one-time boot option (Sandisk Cruiser Ubuntu LTS2.0), the server booted onto my HDD original drive C: instead. I reformatted the USB stick using windows disk tools and repaired it using DiskGenius and then reinstalled the bootable ubuntu live 20 LTS onto it again with the built in linux create startup disk tool... Then the poweredge server finally let me boot back into ubuntu live. I also decided to copy and paste the partitions using gparted rather than clonezilla as it didn't require more software/rebooting. I also changed the boot flags of the grub partition and verified the partition type was GPT. The result I believe is an identical clone. Will have to test now!

---

### Post by CelticWarrior on 2021-04-06
UEFI mode (and GPT) is the default and the recommended mode for any UEFI hardware.
The question then is why people insist on using Legacy mode when there's absolutely no need? Nostalgia?

---

### Post by techmasterdesign on 2021-04-06
Of course it failed to boot to the new SSD so now i'm going to attempt to reinstall grub on the new SSD boot partition.

---

### Post by oldfred on 2021-04-06
Your gpt may also need repair.
With gpt you have primary partition table, partition and backup partition table at end of drive. They all must match and have no duplicates with other drive.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

---

### Post by The Cog on 2021-04-06
> The size of the NVME SSD is listed as 480GB but was actually 447GB
You are probably confusing GigaBytes (1 GB = 1000000000 bytes) with GibiBytes (1GiB = 1024*1024*1024 = 1073741824 bytes).
480 GB = 480000000000 bytes
447 GiB = 479962595328 bytes.
Whatever software is telling you it is 447 GB is using the wrong symbol.

Just me feeling in a pedantic mood.
Incidentally, you can dd from a smaller to a larger drive with no issues other than it won't use the rest of the drive. You can re-size the partitions and their file-systems later.

---

### Post by techmasterdesign on 2021-04-06
Do I need to create a Virtual Disk with the Dell System Setup and then add my grub boot partition and data partition? 

Because as of now it's saying the SSD is unconfigured.

Update: I'm so tired of this.  Been working on it for hours. Just going to reinstall linux on the new SSD then restore from a backup.

---

### Post by QIII on 2021-04-06
A techmasterdesign:

1.  Do NOT use unacceptable language and invoke the asterisks.

2.  Use code tags to surround all command line inputs and outputs.  That preserves formatting and makes your posts more readable.

3.  Use the default font and color.

4.  STOP editing your posts after you have received responses.  You have succeeded quite well in creating an entirely disjointed thread at this point.

Since this thread has now lost cohesion, I am closing it.  Feel free to start another thread if you need to, but bear in mind what I have asked.  If you have any questions about what I have asked, please see the two links in my signature.

---

