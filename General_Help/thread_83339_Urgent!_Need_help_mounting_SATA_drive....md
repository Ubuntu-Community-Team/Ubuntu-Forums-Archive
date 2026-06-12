---
title: "Urgent! Need help mounting SATA drive..."
date: 2005-10-28
forum: General Help
---

### Post by blueturtl on 2005-10-28
I'm at my in-law's and they have one SATA hard-disk which has data they need accessed. I don't know where the device file for a SATA drive is placed, so I could mount it.

The drive is located in sata raid1 on the mobo.

Also, since the file system is NTFS, is there any way to have read rights for the default user when using the live cd for the particular volume? Write rights aren't necessary.

---

### Post by blueturtl on 2005-10-30
Ok, situation's over so I guess I'd only be interested in an answer for knowledge bits.

In case anyone was wondering, I resently had to (re)install Windows XP on a system that had been completely hosed. The problem was, that no matter what I did I couldn't get web access through LAN to work - so I thought to rule out the possibility of damaged hardware I inserted the Ubuntu 5.04 Live disc and tested the system. Everything "just worked". Sound, video, network - everything! My brother in law was going "How come Windows can't just work?". I promised him I'd lend him the Live disc for the time being until we figured how to get Windows back online. He wanted to listen to his MP3s which were on a Serial ATA disc and that's why we would have liked to have it mounted. Anyway, now that Windows is working again there's no point anymore. I see a potential convert though, as he said he'd definately want to use Linux weren't it for the fact he's a total gaming looney. :D

---

### Post by Decon1 on 2005-11-22
Here's the deal!

First you make a directory:

sudo mkdir /media/windows

Next you mount the HDD:

sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,unmask=0222

sudo: Command prompt
mount: Command issued
/dev: device
/sda1: SATA HDD 1st partition
/media/windows: The directory you created
-t ntfs -o nls=utf8,unmask=0222: The rest of the story :-)

The directory was created first attempt but I had issue the mount command twice for it to take!
GL,
Decon

---

