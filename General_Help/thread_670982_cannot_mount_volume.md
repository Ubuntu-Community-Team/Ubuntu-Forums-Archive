---
title: "cannot mount volume"
date: 2008-01-18
forum: General Help
---

### Post by wawarren on 2008-01-18
Hello,  I've got a pretty bad problem here.  I'm running Ubuntu from  the install CD now since I can't get past a Grub Error. 

Long story short I put my system on hibernate for the first time tonight and Ubuntu refused to come out of hibernation.  I was forced to manually shut the system down, and now my disks are screwed. 

I get this error when booting. 

Grub loading 1.5
Error 2
.....

Pretty bad stuff.   So, I read countless forum posts, etc.  Nothing in my Bios is messed up. I've been running Ubuntu 7.04 64 bit for around 6 months flawlessly.  

The problem was the hard shut-down.  I checked out my disk partitions with Gparted from and the Swap seems fine, but my other 2 are in bad shape.  So, this is where I used fsck /dev/hda1 etc. etc. and attempted to fix them up.  It worked sort-of.  I can now mount my partition that contains my data.  Thats good, so I at least don't lose stuff. 

However, my boot partition, which is 14 Gb won't mount even after repairing it. 

Here is the output from dmesg tail

```
[  186.150746] lp0: using parport0 (interrupt-driven).
[  186.718339] ppdev: user-space parallel port driver
[  193.470334] eth0: no IPv6 routers present
[  204.693529] Bluetooth: Core ver 2.11
[  204.693580] NET: Registered protocol family 31
[  204.693583] Bluetooth: HCI device and connection manager initialized
[  204.693588] Bluetooth: HCI socket layer initialized
[  204.864730] Bluetooth: L2CAP ver 2.8
[  204.864736] Bluetooth: L2CAP socket layer initialized
[  204.876601] Bluetooth: RFCOMM socket layer initialized
[  204.876617] Bluetooth: RFCOMM TTY layer initialized
[  204.876620] Bluetooth: RFCOMM ver 1.8
[  253.176557] EXT3-fs: journal inode is deleted.
[  269.871649] kjournald starting.  Commit interval 5 seconds
[  269.871741] EXT3 FS on hda3, internal journal
[  269.871748] EXT3-fs: mounted filesystem with ordered data mode.
[  282.816882] EXT3-fs: journal inode is deleted.

```

By the way, the Grub error changed from "Error 2" to an "Error 15" now..  

Does anyone have any guidance for getting my first partition mounted again?  This has really turned into a nightmare.  You would think my disk would be able to withstand a hard shut-down :(

Reinstalling is now an option since I can recover my data, but with all the applications and specific settings I'm using it could take a month to back to where I'm at now, so naturally that is hopefully a last resort. 

Thank you kindly,

Alan

---

### Post by tgilber1 on 2008-01-18
If you're getting an error message 2, it means that select disk does not exist.

Below is an excerpt from [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

"This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system."

When you boot up you could try the following:

[LIST=1]
[*]Press ESC key to get into GRUB menu
[*]Press the 'c' key to get GRUB CLI [command-line interface]
[*]From the point forward, if you can use the tab key to find out available commands.  This especially useful when partially finishing commands.  Omit quotes below when using commands.
[*]Type "root (hd" -   #use tab key to view available hd - (e.g., "root (hd0,0)")
[*]Type "kernel /", then use tab key to see if you can find available Linux image files
[*]Keep repeating 4 and 5 for each hard drive and associated partitions
[/LIST]

Once you find correct partition, go back to GRUB menu configuration by pressing ESC key and change the root disk/partition to match the correct disk you just found.

---

### Post by wawarren on 2008-01-18
Just to clarify, I get a Grub Error 15 now.  I understand that Grub can't find something that it's looking for, and it's most likely due to my Disk being forced to shut-down. 

I can't do anything in the boot menu.  "Esc" key does nothing. My only hopes are to fix this from the boot CD I think. 

How can I fix my partition if it won't mount?  I've tried fsck, but I don't know much about this stuff.

Just to clarify, I have 3 partitions.  All format as Ext3

/dev/hda0 14 GB - Contains Linux + Boot stuff  (will NOT mount)
/dev/hda1 - Home - 95 GB  (Healthy)
 /dev/hda2.  - Swap - 3 GB  (Healthy)

All of these are on a new Seagate Barracuda Ultra ATA 100 drive which I purchased just before installing Ubuntu 7.04 back when it came out.  

If I wanted to install Linux over again, would it be able to use my Home drive without overwriting it? I would rather do this last resort, but I'd like to know how just incase. 

Thanks again

---

### Post by wawarren on 2008-01-18
I just tried Super Grub ISO CD and it can't find the necessary files to boot either.  I would attempt to place grub on my MBR, but I have Windows on a RAID 0 with two SATA drives so that won't work. 

Just curious, do I even need Grub installed since I swap OS's with the Bios?  I'm a noob, but I don't see why I even need it.   


Anyhow, I still can't figure out how to repair + Mount my 1st partition.  Is there anything else I can do?


Sorry if this should have gone to the extreme beginner section.  

Thanks

---

### Post by tgilber1 on 2008-01-19
Yes, you need a bootloader to get into Linux - GRUB or Lilo.  As for Windows, you do not need GRUB, and you stated, you can boot into Windows directly since Windows is installed on its own disk.  Did you try to find the partitions using the GRUB command line interface during boot-up?

---

