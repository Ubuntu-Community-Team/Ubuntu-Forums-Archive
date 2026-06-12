---
title: "best to backup mixed system - Ubuntu and win"
date: 2018-08-23
forum: General Help
---

### Post by Kris_M on 2018-08-23
Had/have win7 and win10 and relied on EaseUs to backup and restore drive and any of 5 ntfs partitions on SSD to second HD spindle.

When have added Ubuntu in the past i have always relied on Clonezilla(boot to USB stick), but it is slow(1/2 hour).

Enter Ubuntu yet again... and a 500GB ext4 partition on that 2nd spindle SATA3 for backups. Boot grub at the moment.

Looking for alternatives to Clonezilla that are faster and get all the superblocks, etc, :) and yet can reliably 5 restore windows ptns.

EaseUs can't. Someone mentioned Acronis but it doesn't look "at home" in Linux. Must play nice withBIOS/MBR. Macrium apparently can but can't reliably mount ext ptns.

The prob with things like rsync is that I am NOT command line fluent and never will be. I need to be able to boot to a stick and restore whatever. I have gparted on a stick so I can prep the SSD however I need. This also lets out things like dd - btdt :(

Need reliable and fast.

Thanks!

I am assuming that Linux will belly-up on me yet again (last time it was because it wouldn't boot because on box and swapped Nvidia card and couldn't get in no matter what and had to restore partitions individually...)(Clonezilla saved me but I was back at win)

The real problem is being able to restore a partition (win or linux) to a blank disk (because it has been hosed) and have it correctly set up the MBR or whatever win and/or linux needs to boot.

---

### Post by rbmorse on 2018-08-23
I"ve been using Macrium Reflect on my mixed machines since version 4 and haven't noticed a problem with ext partitions.  Don't use LVM but that may make a difference.  I don't think it's any faster than Clonezilla when working ext file systems, though.  Just a lot prettier.

---

### Post by Kris_M on 2018-08-23
> **rbmorse said:**
> I"ve been using Macrium Reflect on my mixed machines since version 4 and haven't noticed a problem with ext partitions.  Don't use LVM but that may make a difference.  I don't think it's any faster than Clonezilla when working ext file systems, though.  Just a lot prettier.

Thanks - I went to try that and both macrium sticks refused to recognize my backup HD (which had 500gb ntfs and 500gb ext4) That is scary soince all my backups are on that HD and I've been making them with win10.  Better go figure that out! I see it flickering when macrium stick is booting but gone when it's up...

---

### Post by Kris_M on 2018-08-23
well, I discovered that my 2 macrium sticks wouldn't recognize my secondary HD, so made a new stick of 3317 and that did. However, it wants about 45min to backup the SSD. Booted to win10 and it wants 27 min to back it up.  This is a chunk slower and speed is maybe 700Mb/s vs 1Gb/s before I chopped that 1T HD in half and put an ext4 in the top half. I am defragging it now to see if that helps (2 more hours).

---

### Post by Kris_M on 2018-08-24
Yeah, defragging helped. when I cut it in 2 it caused a lot of fragmentation. It took 20 min running it on win10. But left me with almost nothing on the 500G ntfs. I will time the next clonezilla more exactly next time - I just approximated it as being 1/2 hour. Probably a 2T HD in my future - just didn't want to drop 100 at the moment... what opsys do you run Macrium on, or standalone?

---

