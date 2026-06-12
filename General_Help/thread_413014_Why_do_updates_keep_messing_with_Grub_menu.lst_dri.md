---
title: "Why do updates keep messing with Grub menu.lst drive assignments?"
date: 2007-04-18
forum: General Help
---

### Post by dwasifar on 2007-04-18
**Short version of issue: **
Update manager updates keep changing /dev/sda to /dev/hda within grub's menu.lst file, forcing manual edits to restore it.

**Long version of issue: ** 
I was migrating a Dapper installation that I had been using as a personal file server.  The old machine had system drive and storage drive at /dev/hda and /dev/hdb respectively, and a CDROM at /dev/hdc.  The new machine's system drive and storage drive, being SATA, are at /dev/sda and /dev/sdb, and the optical drive at /dev/hda.  

I used a drive cloning program to copy the old /dev/hda to the new /dev/sda, and the old /dev/hdb to the new /dev/sdb; booted to a live CD and resized the partitions appropriately for the new larger drives.  I mounted the new system drive, still under live CD, and edited the following: /etc/fstab, to mount the new drives correctly; /etc/iftab, to correctly identify the new machine's network card as eth0; /boot/grub/device.map, to point hd0 to /dev/sda; and /boot/grub/menu.lst, replacing all instances of /dev/hda with /dev/sda.  Having done this, I booted from the hard drive and (aside from having to reconfigure X) everything was entirely normal.

Seeing as how we're going to have Feisty tomorrow, I decided I didn't want my new server to be TWO versions behind, so I decided to update to Edgy, which I did using update-manager -d -c.  This seemed to complete successfully but on boot the system hung at the splash screen with only a small amount of progress on the bar.  I took the easy way out of this, and repeated my clone-and-edit procedure to get back to a known good Dapper configuration.  Then, instead of directly doing a version update, I let update manager install the 95 or so pending Dapper updates.  Again, this seemed to work, but again, it wouldn't get past the splash.  However, since the Dapper installation is not Quiet, I could see it was hanging while trying to load the root partition.  So I went to menu.lst and found that all my /dev/sda edits had reverted to /dev/hda.  I reapplied the edits and the machine then booted normally to Dapper.  Sensing a pattern, I did another Edgy upgrade, and after that was complete I found that once again, the /dev/hda's were back in menu.lst.  I reapplied the edits *again*, and the machine then booted normally to Edgy.

Why is this happening?  Will it continue to happen every time there is an upgrade that affects Grub?  Is it because I have an optical drive at /dev/hda?

---

### Post by bwhite82 on 2007-04-18
It is my experience that this happens everytime you update grub, I would backup your menu.lst and replace it after the upgrade or simply keep editing the way you have been. Check Launchpad for a bug.

---

### Post by dwasifar on 2007-04-18
Or I could pin the current version of grub in synaptic, I suppose, if THAT worked in Edgy.  Maybe it will work in Feisty.

Thanks for the info.

---

### Post by dcstar on 2007-04-18
> **dwasifar said:**
> **Short version of issue: **
Update manager updates keep changing /dev/sda to /dev/hda within grub's menu.lst file, forcing manual edits to restore it.
........
Then, instead of directly doing a version update, I let update manager install the 95 or so pending Dapper updates.  Again, this seemed to work, but again, it wouldn't get past the splash.  However, since the Dapper installation is not Quiet, I could see it was hanging while trying to load the root partition.  So I went to menu.lst and found that all my /dev/sda edits had reverted to /dev/hda.  I reapplied the edits and the machine then booted normally to Dapper.  Sensing a pattern, I did another Edgy upgrade, and after that was complete I found that once again, the /dev/hda's were back in menu.lst.  I reapplied the edits *again*, and the machine then booted normally to Edgy.

Why is this happening?  Will it continue to happen every time there is an upgrade that affects Grub?  Is it because I have an optical drive at /dev/hda?

There is possibly a config file buried somewhere from the original installation with the setting to install Grub on the original /dev/hda device, and each time a Grub update occurs it uses this setting.

It may well be a "feature" to ensure that people are able to recover their original Grub setup if something got corrupted in the future.

I would recommend running the manual Grub setup inside Grub itself using the new sda device (as per the instructions in the various "Restore Grub" HOWTOs). This may fix thing permanently.

---

### Post by louieb on 2007-04-18
Look in the automagic section. I bet your** kopt= **is the culprit. and while your there check the **groot=** also but I bet that is ok.

---

### Post by MetalMusicAddict on 2007-04-18
Honestly do a clean install and you should be cool. There some things going on with The way drives are assigned. I have a server with 2 PCI IDE controllers and 8 drives. I dont want to get started on what a nightmare that has been.

Do a clean install from a "Alt" disk and define all the mount points on install and you should be golden.

---

### Post by dwasifar on 2007-04-20
> **louieb said:**
> Look in the automagic section. I bet your** kopt= **is the culprit. and while your there check the **groot=** also but I bet that is ok.
Wow, thanks!  That was it, all right.  I didn't change it because it was a commented line, and I didn't even think of it.  Sometimes the easy ones are the hardest.  

Thanks!

---

