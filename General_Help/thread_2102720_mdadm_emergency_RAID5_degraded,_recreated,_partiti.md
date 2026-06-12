---
title: "mdadm emergency: RAID5 degraded, recreated, partition problems??"
date: 2013-01-08
forum: General Help
---

### Post by codemaster on 2013-01-08
So today I received an automated e-mail from my RAID array system as follows:

```
This is an automatically generated mail message from mdadm
running on cyrus

A Fail event had been detected on md device /dev/md/2.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdf2[2] sdg2[3] sde2[1] sdd2[0]
      11002368 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
md2 : active raid5 sdf3[5] sdg3[3] sde3[1] sdd3[4](F)
      2185873920 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [_UUU]
      
md0 : active raid5 sdf1[2] sdg1[3] sde1[1] sdd1[0]
      437760 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
```

So when I got home, I rebooted into a live CD, and did a mdadm --assemble --scan. It created my /dev/md2 just as stated above. I tried to --re-add the /dev/sdd3, but it simply would not add.

I googled a bit and found one guy suggesting a mdadm --create --assume-clean. I should have known this was a bad idea, but did it anyway. I loaded up gparted immediately afterwards and, strange ... my partition isn't there. Well, okay then. I decided to try recreating my RAID as degraded at least.

I tried stopping and re-creating the array via mdadm --create --assume-clean but leaving the sdd3 as 'missing' instead. Again, gparted now shows my partition as unknown.... :(

What should my next steps be? There's very important data on here that as yet to be backed up, so I'm extremely worried right now.

Thanks guys, I really appreciate the help.

---

### Post by codemaster on 2013-01-08
One thing I noticed when trying to figure out how to perhaps properly re-assemble my array is that it is assembled in a bit of a weird format:

md2 : active raid5 sdf3[5] sdg3[3] sde3[1] sdd3[4](F)

Could this be why the re-creation of the array failed? If so, how would I properly order them in this way?

I also read online somewhere that a guy had luck zeroing out his superblock and having mdadm attempt reassmbling. Not sure if that would work in my case or not, but I have yet to try.

---

### Post by codemaster on 2013-01-08
Reading over a bunch of articles, it seems that a **possibility **is as follows:
- Create the mdadm array with missing disks for the missing disk slots (mdadm --create /dev/md2 --assume-clean missing /dev/sde3 missing /dev/sdg3)
- Add the disks that are in the later slots of 4 and 5 (mdadm --add /dev/md2 /dev/sdd3; mdadm --add /dev/md2 /dev/sdf3)

...Possibly this will work? I'm curious if anyone can give me a sanity check before I try it out

---

### Post by SaturnusDJ on 2013-01-09
> **codemaster said:**
> 
I also read online somewhere that a guy had luck zeroing out his superblock and having mdadm attempt reassmbling. Not sure if that would work in my case or not, but I have yet to try.

After zeroing mdadm superblocks, assembling becomes impossible.
You did an --create already, so the originals are gone anyways.


Check out [http://ubuntuforums.org/showthread.php?t=2100781](http://ubuntuforums.org/showthread.php?t=2100781).
Now it's important for you to --create using the same order as when you did when creating them for the first time.

When the information in your first post is right, it should be:
```
sudo mdadm --create /dev/md2 /dev/sde3 /dev/sdg3 /dev/sdd3 /dev/sdf3 --assume-clean
```

But I doubt this, and when I compare with your other arrays I think it is:
```
sudo mdadm --create /dev/md2 /dev/sdd3 /dev/sde3 /dev/sdf3 /dev/sdg3 --assume-clean
```

It should be safe to try both, and see if you are able to mount and filesystem. If one doesn't work, just stop the array and try the other, _do not_ start to edit partitions and such!

If /dev/sdd3 fails, you may put the "missing" at it's exact place in line.
You can't use "missing" more then one time if you want to start a RAID5 array.

---

