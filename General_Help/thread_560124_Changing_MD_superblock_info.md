---
title: "Changing MD superblock info"
date: 2007-09-25
forum: General Help
---

### Post by unperson on 2007-09-25
I'm running Ubuntu Feisty (7.04) on my system here using mdadm RAID devices for my / and /home partitions.  Currently, the two RAID devices show up as /dev/md0 and /dev/md1, respectively.  However, if I run 'mdadm --examine --scan' I get
```

ARRAY /dev/md1 level=raid0 num-devices=2 UUID=8f70...
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=0dfb...

```
showing the two RAID devices as /dev/md1 and /dev/md2.  I believe this may have been the root of some problems I had when I upgraded to Feisty and my system wouldn't boot (problem and solution were discussed at [http://ubuntuforums.org/showthread.php?t=548964]("http://ubuntuforums.org/showthread.php?t=548964")).  It seems like it would be best if info in the MD superblock matched that in the rest of my system (e.g. mdadm.conf) which seems to universally see these as md0 and md1.

So, I have 3 questions:

[LIST=1]
[*]Is it possible to change the information in the MD superblock (while retaining all the data on the RAID)?
[*]Is this a reasonable idea or is there some very good reason not to do this?
[*]How do you do it?
[/LIST]

For reference, my /etc/mdadm/mdadm.conf reads as follows:

```

DEVICE partitions
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=8f70...
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=0dfb...

```

This information agrees with what I see from mount or df.

---

### Post by fjgaude on 2007-09-26
I guess we are all learning, learning as we go.

Do you mount the raids in fstab? in menu.lst?

I wonder if you do if the mdadm.conf file is ever used. It seems, and I could be wrong, that file is used to assist in reassembling a busted array automatically.

Maybe kidders can shed some light on this. The only way I have now is using a real system to test, which is not good. I will build up a test system soon and get answers to all these questions regarding md raid.

---

### Post by Crakie on 2007-09-26
Well, I have some advice for you, but please: be careful as I am not a guru by any means.

I had a situation recently where one of the superblocks in my raid 0 array did not match the other and hence the filesystem could not be mounted. This was in Arch Linux, not Ubuntu. So I basically went on Google and forums to find out the same thing you are asking now: can I change the superblock and if so, would I lose any data? I got no useful answer, so I went on and recreated the array using

```
 mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```

mdadm gives a warning that these drives appear to be part of an array already... ignoring that, I approved the action I requested and everything was in working order again. I believe what this command does, essentially, is recreating the superblocks. I am still worried that some data on the drive may be corrupted, although I have not had any strange things happening for a week of daily use already.

You could try the same, but I would strongly recommend a backup first. Partimage is excellent for that.

---

### Post by fjgaude on 2007-09-26
Thanks, Crakie, for advise. You were the one that got me going with md raid in the first place.

I used the --stop /dev/mdnn to get access to drives that were in an array. Then rebuilt the array, over and over, testing throughput of two drives, then three and four. Now if you have good data on one of the drives, please do backup the affair.

One last thought, you could stop the array, then try to --assemble it again.

---

### Post by unperson on 2007-09-28
Thanks for the input.

I do think the system is using the mdadm.conf, based on what happened before (described in the forum post I linked to), but I do not know how to be certain.  The /etc/fstab file contains the entries for the RAID partitions, but it identifies them by UUID rather than by device name.  The GRUB menu.list has root=/dev/md0.  When I was having trouble before, I believe that it was because it was not using my mdadm.conf file (because it was marked as being unchecked since the update of mdadm by apt) and was instead building one using mdadm --examine --scan, which gave the the assignment of the RAID partition containing / to the location /dev/md1 rather than /dev/md0, so GRUB couldn't find it.

Crackie, your suggestion sounds interesting/promising, but I can also see how it's potentially dangerous.  I might consider going that route, but like you say I'll make sure to back everything up first (most stuff is backed up not, but not everything).

I'm not sure how stopping and re-assembling will help.  Wouldn't it just rebuild it the same way it was (according to mdadm.conf)?

Anyway, another option it to leave the MD superblock how it is and just change everything else to match **it**.  I had the impression that it's more standard to make the first RAID partition /dev/md0, so I was trying to match that, but perhaps it's easier to just go with the assignments on the superblock, which start with /dev/md1.  If I did change "everything else" to match that assignment, I'm not sure what all I'd have to change.  I guess I'd have to alter mdadm.conf, menu.list, and rebuild the initramfs image to reflect the new settings.  Would that cover it, or are there other things I'm missing?

---

### Post by Crakie on 2007-09-28
> **unperson said:**
>  I guess I'd have to alter mdadm.conf, menu.list, and rebuild the initramfs image to reflect the new settings.  Would that cover it, or are there other things I'm missing?

Yes, I think that should cover it. You may want to rename your existing mdadm.conf and recreate one with: 

```
mdadm -D --scan >> /etc/mdadm/mdadm.conf
```

Rebuild the initramfs image next.

---

### Post by fjgaude on 2007-09-28
To lend to the confusion, at least on my part, I can only mount my raid5 MD32 array using the UUID that blkid provides, and not the one that mdadm --scan shows.

Boy, one of these days soon, I'm gonna play around and learn all the ins and outs of mdadm, but only on a test set of disks.

Thanks to all that have helped me along the way.

---

