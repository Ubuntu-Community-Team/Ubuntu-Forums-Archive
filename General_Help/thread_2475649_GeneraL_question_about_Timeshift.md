---
title: "GeneraL question about Timeshift"
date: 2022-06-03
forum: General Help
---

### Post by cscj01 on 2022-06-03
I've just started using Timeshift, and a thought occurred to me.  If my system device goes bad, and I install a new device, can I restore from Timeshift to the new device by booting from an installation CD/DVD or USB drive without having to reinstall Ubuntu?

---

### Post by TheFu on 2022-06-03
Most Ubuntu issues can be solved without a reinstall. The specific details are what determine if this is possible or not.

When you reboot into a "Try Ubuntu" flash drive, you'll need to install timeshift and connect up the storage that holds the backups, obviously. If you need specific steps, there are lots and lots of web articles about this:  "_restoring to new HDD using timeshift_" was my google search term.

Any backup tool can be used at different levels. The choices made by the person setting up the backups determines whether that backup gets everything needed to boot or not. I specifically DO NOT backup the boot or OS files. Why bother, since those are trivially reinstalled?  I do backup system data, system settings and personal data, personal settings, however. I also backup a list of manually installed packages, to make reinstalling those fast.  From these things, the system can be restored from a minimal install in 45min or less.

There's a point where trying to solve any issue is less efficient than performing a fresh install.  That's always the question for each person to answer.

If you have excellent backups, then a fresh install AND restoring the system to what it was before the problem is 30-45min, so troubleshooting issues more than an hour really doesn't make any sense, unless you are just driven to know the answer.  If you just need to get working again, the why isn't as important as the getting back to work ASAP.

If your backups can't restore the system to completely new hardware or the current hardware in under 45 min, then I say you are doing backups wrong.

Image-based backups are almost always "wrong", IMHO. They don't address malware attacks and most people don't retain 90 days of versioned backups - who has 90x the storage just for backups?  With file-based backups and efficient backups that recognize differences over time, 90 days doesn't take even 1.5x the storage. I see 1.3x on desktops - that's just the files that change as outlined above, not the OS.  My main desktop only has 8 GB of stuff backed up.  90 days with a new version every night is using 12.6GB of storage. **Why wouldn't you have 90 days if it is just 13G of backup storage?**

Timeshift operates in 2 very different modes depending on the underlying file system used.  Using a file system (or volume manager) that makes backups unlikely to have corruption is smart. When the underlying file system is btrfs, this can be accomplished using the BTRFS snapshot facility.  
When the underlying file system is not BTRFS, it falls back to using rsync, which allows files to change in the middle of the backup process. Not having corrupted backups is important for servers and automation.  

For desktops, it is slightly less important to avoid corruption and we may go years without seeing any corrupted files in the backups, but they do happen. Ask any admin who's worked inside an enterprise with hundreds to 100K+ servers. She knows that corrupted files happen all-the-time during backups.  Where I worked, we'd see backup issues nightly across our projects' ~100 servers because files were being written during the backups.  There were some specific files which were critical to backup and always being written. For those, we used alternate backup methods (usually a DB dump to text) to ensure they could be restored clean.

Reinstalling a minimal ubuntu is 10-15 minutes these days.  Not a big deal and there's little need to backup the OS since it is so easy.  About once a year, I need to restore a system for various reasons, so my backup+restore methods are validated.  It usually happens because the admin (me) did something stupid.  Plus, I know that there is a backup from 2am last night, so perhaps I'm a little more willing to screw around with some non-critical systems.  The restore process is a good way to clean away cruft from the last system LTS-to-LTS upgrade, so I see it as an opportunity to be completed in 45 min on the way to a faster, cleaner, less-crufty, system. ;)

---

### Post by cscj01 on 2022-06-03
Thank you for your very thorough and reasoned reply.  For years I used clonezilla to do backups of the filesystem disk.  It was a pain to keep it somewhat current because I had to shutdown to run it.  I ran across Timeshift a few weeks ago, set it up, and began using it.  It really seems to be what I need.  Your point about BTRFS is well taken.  I have used ext4 for quite a while, so I'll need to do a little research about BRTFS.  Thanks again for your rersponse.

---

### Post by TheFu on 2022-06-03
BTRFS has some warts and some failure modes where data corruption is much more likely.  In a single-disk system, say a laptop, I think the risks to using btrfs are minimal and it would be a good choice, unless you runs virtual machines or any CoW layered file systems.

Some of those BTRFS failure modes are explained here: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)

I don't have BTRFS on any of my systems. I use LVM for volume management and snapshots. Also, I don't use timeshift, but can see where it would be a reasonable backup tool for many people.  I think BTRFS + Timeshift would be an excellent setup, within the caveats of a single system, no VMs, and no CoW layered file systems like LXD almost demands.

Timeshift doesn't fit my needs, but that doesn't mean it can't be used by others.  There are 50+ backup tools out there. Each with pros and cons. Lots of people swear by timeshift for OS backups, but they all seem to use something else to backup their data, which I never understood.  That's my biggest issue with timeshift. I want 1 backup tool and handles everything efficiently. Why become expert at 2 tools when only 1 should be necessary?

---

### Post by cscj01 on 2022-06-03
You are right about people using two separate backup programs to back up system and data.  Years ago I found luckyBackup and began using it to back up my data.  It uses rsync, and I was familiar with that.  Timeshift allows me to automate my snapshots of the system, but I do use rsync for my ext4 system disk.  As you mention, BTRFS would be an issue for me at the moment because I have VMs as well.  One finds something that satisfies a need at a given point in time, and there is a tendency to stay with it if it works for you.  I was still using two separate programs for system and data before Timeshift, because I was using clonezilla for my system backup.  I had used that for years, but I hated it because I had to shut my system down.  So when I found Timeshift, it seemed a good way to get away from clonezilla.  I could have used luckyBackup, but I thought Timeshift offered a little more.  C'est la vie!

---

### Post by TheFu on 2022-06-03
You could have used other cloning tools like **fsarchiver** while the system was running, provided you'd use LVM and created a snapshot to be captured.  True snapshots are a fantastic tool, but most users have been been told that their backups are "snapshots", which usually isn't the situation.

Any chance you are going to SELF in June? It's in Charlotte again.

---

