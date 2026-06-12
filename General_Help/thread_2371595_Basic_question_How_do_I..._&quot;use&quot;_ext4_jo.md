---
title: "Basic question: How do I... &quot;use&quot; ext4 journaling?"
date: 2017-09-16
forum: General Help
---

### Post by david503 on 2017-09-16
Ok, so, I have 16.04 and I switched to gnome since unity is being phased out anyway.

After I got gnome running, everything was fine, and then I installed a plugin which froze everything so I restarted.  It wouldn't come back up. I can get into recovery mode on the initial purple screen, etc., but I don't know what to do. 

(I have 20 years of lamp development, so you can throw stuff at me, I'm no beginner!)

How do I "use" ext4 journaling?  It's enabled by default, right? I never explicitly turned it off.  

When I boot from a live cd, and I look at the drive, it has about 200 gig missing.  But I'm sure it must all be there. 

Your instinct is to blame the hardware, but.... nothing changed except installing that plugin.  This isn't a coincidental hard drive crash, it directly correlates to that moment.  

I swear the drive must be physically fine, I can even get in to get files from it when I get into shell in recovery mode.  It's like there was just some slight alteration in the FS.  

So, I know ext4 has journaling but how do I employ it?  Like, "hey, ext4, do your journaling thing!"  How do I use journaling?

I googled for "use ext4 journaling" and it was all about turning it on or off... No, how do I, um "use" it?

Thanks,

d

---

### Post by TheFu on 2017-09-16
It is part of the manner in which data is written to the disk.  You don't turn it on or off like you can with the journals in ext3 (which effectively makes the file system ext2).  Think of a journal as a 2-phase commit for all disk writes.  Until the 2nd write completes, the 1st isn't removed.  That means if something prevents the 2nd write for any reason, then the journal log can be *replayed* to make the final commits later, perhaps after a reboot.  The wikipedia article on this isn't bad, BTW.

---

### Post by sudodus on 2017-09-16
How fresh is your backup?

[hr][/hr]
1. If the backup is very fresh (and complete), I would simply go back to  the backed up version.

[hr][/hr]
2. If a lot of important information is not backed up, I suggest that you try hard to recover that information.

It is a good idea to **clone** the problematic drive to another drive of the same size or bigger. The following link describes how **ddrescue** can be used for this cloning task, even with a drive with bad sectors.

[[scroll down to find the relevant paragraphs] Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

Then you can do the recovery work on the cloned copy. If something unexpected happens, you still have the original drive and can make a new cloned copy.

- Check the S.M.A.R.T. information of the drive to get an indication of the health of the hardware. You can find this information via **Disks** (when booted from a live DVD disk or USB pendrive or memory card). See this link

[[scroll down to] Maybe the disk hardware is damaged](https://askubuntu.com/questions/948036/reformating-hard-drive-after-malware-damaged-boot-sector/948560#948560)

- If you have not tried to repair the system with **e2fsck**, please do it now (on the cloned copy)

```
sudo e2fsck -f /dev/sdxy
```

or if you suspect bad blocks
Code:

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number, for example /dev/sdb1 for the first partition in drive b.

- After that you can try with more advanced repair tools, first **testdisk**, then **photorec** (which is often the the last resort unless you use professional tools).

---

