---
title: "How do you do automatic backups?"
date: 2013-06-16
forum: General Help
---

### Post by ladasky on 2013-06-16
Hi, everyone.

I just upgraded to 13.04.  Since 8.04, I have operated a system with two hard drives, configured in RAID1 using *mdadm*.  The 13.04 installation would not cooperate with my existing configuration.  Reluctantly, I tore the whole thing down. I have 13.04 installed on just one of my two hard drives for now.

I also do regular backups to an external hard drive, but my RAID saved me a lot of hassle when one of my two internal hard drives failed (under warranty).  I was able to disassemble the RAID, and run with the remaining drive for a week or so while I waited for the replacement.  When I got the replacement drive, I reassembled the RAID and it synced up automatically.

So, I no longer have *mdadm*.  However, I set 13.04 up using LVM, which is what the Ubuntu installer was hinting I should do.  I have separate boot, root, and home partitions, plus one spare partition that I intend to use as root for a future version of Ubuntu.  I know that I have options from this point, even if it's not *mdadm*.  What I would like is something which, if it doesn't run quite as transparently as RAID1, gets close.  If one drive fails, I want a second, bootable mirror.

What would you recommend?

---

### Post by Cheesehead on 2013-06-16
Redundancy and backup are not the same. It's difficult to figure out from your description which is your goal.

---

### Post by carboi82 on 2013-06-16
I believe you can still download and install mdadm with no issues on 13.04, its just that its no included in the standard distro any longer.

---

### Post by ladasky on 2013-06-16
Thanks for your replies, Cheesehead and carboi82.

I have a USB external drive for manual backups.  I set up a USB drive once to be bootable.  It was usable, but slow.  I would also like a backup to my second SATA drive, which I definitely want to be bootable.  (That's right, three copies of my data in all.)  That was achieved by the RAID1 I used to have, but I am willing to accomplish it in other ways.  

An LVM mirror seems like a logical way to proceed.  I may be wrong.  Does anyone out there use this approach?

A *cron* job that runs *rsync* as root might, or might not, do the job.  If changes are made to the deep structure of the partitions, or to the contents of a non-Linux partition (such as boot), maybe *rsync* would be the wrong tool? It might also be overkill for certain tasks.  When I booted my Windows Vista virtual machine and made tiny changes to it, RAID made just those changes, in parallel, on the two hard drives.  It was quick and transparent.  When I backed up my RAID to the external drive, *rsync* would have to rewrite the entire 50 GB virtual machine, even though perhaps only a few megabytes of it had been changed.

You can indeed download and use *mdadm* while running 13.04 from the live CD.  I don't think that *mdadm* was ever included in the standard distro.  It was included in the alternate distros, however.  I used *mdadm* to define my RAID (actually, to redefine it for 13.04).  But *grub-install* _[failed on this configuration]("http://ubuntuforums.org/showthread.php?t=2140218")_, no matter what I tried.  

The Ubuntu 13.04 installer pretty much tells you to favor LVM.  I took the hint.

---

### Post by Cheesehead on 2013-06-16
Well, I favor backup over redundancy. Once each day, triggered by cron or anacron, my laptop uses rdiff-backup to login to a server and push the backup sync. The server has a raid array (using mdadm), and it's only data-backup, not a mirror, and the backed-up data is not bootable.

There is also a bit of setup, telling rdiff-backup exactly which data should be saved (/home except machine-created files, custom /etc configs, my created stuff in /usr, etc)...but that just makes me keep stuff better organized.

When my laptop drive fails, I install the new one (I have a spare), install a fresh copy of Ubuntu (I have a USB stick), teach it how to ssh, install rdiff-backup, and then restore the data.

I'm not a fan of booting from a raid array - I think it makes booting slower and more complicated than it needs to be.

---

### Post by agillator on 2013-06-16
If you are considering a periodic backup you might take a close look at rsnapshot. I believe it works with RAID arrays without problem but that is not my area of expertise. It is simple, quick (based on rsync) and normally is scheduled through cron though backups can be run manually. It is also quite flexible. At the beginning configuration may be a litle confusing, but once you understand their thinking it is really quite easy.

---

### Post by ahallubuntu on 2013-06-16
~

---

