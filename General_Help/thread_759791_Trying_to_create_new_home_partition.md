---
title: "Trying to create new /home partition"
date: 2008-04-19
forum: General Help
---

### Post by elashish on 2008-04-19
Hello

I'm trying to create a new /home partition so I can upgrade to 8.04 at some point soon, but I have no idea plan it out.

Here's a screenshot of my current setup. Right now I have a dual boot setup and my first priority is to make sure that nothing gets screwed up. But if it's possible, I'd like to create the new partition out of sda1 (where I have windows installed). Is this possible?

---

### Post by lswest on 2008-04-19
wait, you already have a /home, right?  you can use that one in 8.04 as well, just specify it during install as "/home" and choose not to format it.  Is that what you meant?  or did you want a new root filesystem? if so you can reformat sda1 as ext3 and mount it as "/" and leave the /home as that, do not format it, and mount it (from the manual partitioning page) as "/home"

---

### Post by elashish on 2008-04-19
Well see, right now I have /home on my / partition. I'm fairly certain that it won't get wiped when I upgrade, but it would nevertheless be nice to keep it separately in case something goes wrong.

Won't I lose my windows partition if I reformat sda1?

---

### Post by lswest on 2008-04-19
well, if you have your /home on the same partition as / then it will get wiped, but i see there are 2 ext3 partitions made...can you post the output of ```
df -h
```?

And yes, you'd lose windows if you just reformatted the windows drive (sorry, didn't realize you wanted to keep it).  You can also just resize the windows partition and use the free space, but that shouldn't be necessary if my thoughts about the 2 ext3 partitions are right.

---

### Post by elashish on 2008-04-19
```

/dev/sda3             9.2G  3.8G  5.0G  44% /
varrun                248M   92K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   76K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              18G  9.3G  8.3G  53% /media/sda1
/dev/sda4              64G   45G   16G  75% /media/sda4
/dev/scd0             4.1G  4.1G     0 100% /media/cdrom0

```

sda4 is just a generic storage space accessible from both windows and ubuntu. I'm running out of space on it, so I'd prefer not to take it from there, but if I had to, then I would.

---

### Post by lswest on 2008-04-19
Ah, i see, you made an ext3 partition to share files between XP and Linux, sorry, wasn't expecting that (usually people use FAT32 for that).  Well, what you need to do then is take some space off of either the XP partition or the sda4 (or you can take a bit of both).  To do so right-click choose "resize" and decide where you want to have the free space.  (i'd say for sda1 put it after it, and sda4 put it before) and if you decide to take a bit from both, you'll have to "resize" the partitions between them (basically right-click choose "resize" and don't change the size of the partition, just put the free space before/after the partition, so that all of the free space groups together) and then either leave it or format it as ext3 for the /home folder.  However, you'll have to manually copy over your home folder from the / partition to your newly created home folder if you want to keep your files.  Also, i'm not sure if you can set the new partition to be /home for your current Linux, at least, not without running into issues.

My advice:
resize, create the partition, copy the files over, then do a fresh install of Hardy, and format your current "/" and then set the new partition as "/home" then.

Lastly:
just looked at it all again...your "/" is only 10GB, mostly used already, and generally when i set up a dual partition system for linux, i do 10GB for "/" and 15+ for "/home".  So yeah, maybe think about how best to do it.

---

### Post by elashish on 2008-04-19
Okay, thanks. As I understand it, when I take space from sda1 before, then I'll merge it with sda3 (and probably sda2) and that will erase everything between the newly resized sda1 and sda4. So before that I will have to copy my /home to a flash drive or something?

Also, how much space would /home require?

---

### Post by lswest on 2008-04-19
Actually, i was thinking you resize sda1 (which will create a chunk called "free space" or "unallocated space") and the infos about resizing all the partitions in between were mainly if you decided to take a bit of both partitions, where it was then thought that you would "resize" it and just make the free space before become the free space after and vice versa  (because you can't create partitions using free space unless the free space is all grouped together).  Depends what you want to do really, and home size can vary.  If you want to keep music, videos, photos on there aim for 10GB at the least.  If you have that stuff on your generic storage space, and if you don't plan on wineing many programs, you can probably get by with a bit less.

Maybe post what exactly you want to end up with partition-wise and i can help you figure out how best to do it.

---

### Post by elashish on 2008-04-19
Well I think I'll just keep things like program settings and whatnot on /home, doesn't make sense to put more than that on it.

Here's my plan - remove about 3 GB from sda1, and then merge that with sda2 and sda3 (roughly 15 GB). Then from there, create a new "/" (~10 GB), swap (.5-1GB) and then make the rest /home. Is that feasible? Will it still boot properly? And will it preserve my settings or should I copy them before doing it?

---

### Post by lswest on 2008-04-19
if you merge the 3 partitions you will need to back up your /home and you will need to restore the XP bootloader (there is a link to a how-to i made in my sig - 2nd line) or else install Ubuntu straight after, otherwise you will be unable to boot any OS from your hard drive, as the files required for GRUB will be gone.  Otherwise it should work.

---

