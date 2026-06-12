---
title: "Oh God Oh God Oh God"
date: 2006-07-30
forum: General Help
---

### Post by BetaMaster on 2006-07-30
Shoot me now.
A week ago my Windows installation broke. It got corrupted. It was unrepairable. I installed Ubuntu and have been using it exclusively since. I wanted to back up what files I had on my hda1 drive (that had Windows on it), and eventually install Windows again if I wanted to play some certain games. I tried reinstalling XP today on another partition I had so that I'd be able to begin transferring files (Since I couldn't get write access to either of my NTFS drives). This overwrote GRUB in the MBR, and left me unable to get into Linux anymore. To top it off, the XP install is even more borked. I can only see my primary hard drives, meaning, hda1 and hdb2 (Old Windows and new Windows install). I can't see the data drive I hoped to back up the old Windows data (like My documents, Music, downloads, etc). I can't get internet or graphics drivers to work on the XP install either. I'm on a laptop right now, but it isn't mine, so I can't use it. Help! I need some serious technically assistance right now on how to fix my errors!

I don't think I'll bother going back to XP after this. Too much of a hassle, all it does is break what I already had working.

Thanks so much in advance, I hope to get some replies quickly

---

### Post by BetaMaster on 2006-07-30
Should I install Ubuntu on the second XP partition to get GRUB restored, and then what?
Is there a way to get NTFS HDDs to have read/write access in Ubuntu?

---

### Post by Jagot on 2006-07-30
> **BetaMaster said:**
> Is there a way to get NTFS HDDs to have read/write access in Ubuntu?

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by teet on 2006-07-30
Why do you need write access to BACKUP files from an NTFS partition?  You only need read access...unless your backup disk is formated in NTFS as well?

The easiest solution would probably be to format your backup disk as something Linux can write to (FAT32 or EXT3 would both work).  Hook up all your disks, boot up the Ubuntu live cd and copy all the files from your NTFS disk(s) to the newly formatted backup disk.  Then, unplug your backup disk entirely from your computer, hook up your other disk(s) and install ubuntu.  Finally, hook your backup disk backup and copy all the data back over to your ubuntu install.

-teet

---

### Post by BetaMaster on 2006-07-30
The backup disk is, indeed, formatted in NTFS. I'd format it to something else, except, the backup disk has other files stored on it as well.

Jagot, thanks, I'll try that tomorrow.

---

### Post by BetaMaster on 2006-07-30
Okay I tried what you suggested, Jagot, and ran into even more problems. First, I couldn't get NTFS read/write ability still after following those instructions.

I installed Ubuntu onto the second partition, and got GRUB back. But Ubuntu installed GRUB onto the second partition again, so after I erased the second partition of Ubuntu, I was back to square one with GRUB not working.
How can I get into the MBR and tell it to look for GRUB in hdb1?

---

### Post by o_fortuna on 2006-07-30
Here you go (you'll need an Ubuntu Live or Desktop CD):
1. Pop in the Live CD, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "grub"

4. Type "root (hd1,0)", or whatever your harddisk + boot partition numbers are; I think this is right for you (hda1 would be (hd0,0).

5. Type "setup (hd0)".

6. Quit grub by typing "quit".

7. Reboot.

This will reinstall grub. I hope this works for you.
Adapted from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857")

---

### Post by hawko on 2006-08-01
I had a similar type of issue and just used the Ubuntu Live CD.
Boot from the CD and use GParted to add a partition to your backup drive.  Format it as FAT or EXT3. Backup your stuff from the other NTFS drive and the NTFS partition on that drive (still using Live CD).  Once backed up, do a clean install of Ubuntu on the first drive and recover your files from the backup partition.

---

