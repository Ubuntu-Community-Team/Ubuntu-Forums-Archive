---
title: "mdadm RAID question..."
date: 2013-08-25
forum: General Help
---

### Post by Michael_Beary on 2013-08-25
I have a failed RAID and I'm trying to piece together what happened.  Here's the command that was used to create the RAID:

mdadm --create --verbose /dev/md0 --chunk=128 --level=5 --raid-devices=10 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdm1 --spare-devices=2

With this RAID setup, is there just one parity stripe, and is the fault tolerance only 1?  Two drives failed simultaneously and I'm told that fsck was run.  With two drives that failed, I can't see how the RAID could have been in a clean but degraded state - the RAID would have to be down and fsck could not have been run in my opinion.  Here is what I was told:


SMART reported faulty sectors on /dev/sdj, /dev/sdk, and /dev/sdc.

Those were swapped out with new drives and the array was in a clean but degraded state.
The order of the drives has not been changed.
However, we were getting filesystem (ext4) errors. So, I tried to remount the filesystem but it wouldn't remount.
Saw this kind of error repeatedly:

Nov 29 12:48:50 rmcns1 kernel: EXT3-fs error (device md0): ext3_get_inode_loc: unable to read inode block - inode=650740030, block=1301479435

After much research, ran an fsck to hopefully recover the 9TB filesystem - it ran for about 4 days, but correcting way too many errors though. It was at this point I was no longer sure the fsck was helping matters. So, I killed the fsck, disconnected the array from the host, commented that filesystem out of /etc/fstab in order to get the host back online, and rebooted the server.


It shows three drives as bad above, but one was replaced very early on and the RAID had reconstructed this missing member, after which the RAID ran fine for a month or so.  After this, two drives failed simultaneously and the RAID was completely broken and "down" according to them.  I'm just wondering if I'm not getting the whole story... unless there's a fault tolerance of two drives, I dont see how two bad drives could be replaced with blank drives, and then fsck being run.

Please let me know your thoughts.
[http://www.bouncebackdata.com](http://www.bouncebackdata.com)

---

### Post by Michael_Beary on 2013-08-25
One important thing to note is the two drives didn't fail quite simultaneously.  One failed about 24 hours after the other.  So I suppose one of the spares was being rebuilt into a RAID member - does it sound right that this would take longer than 24 hours?  

So perhaps the second drive failed as a result of the rebuilding stress.  But as far as I know the RAID never did come online as clean but degraded and then the second drive failed.  So I don't know how fsck could have been run after the two bad drives were replaced.

---

### Post by SaturnusDJ on 2013-08-25
One parity stripe, yes. Fault tolerance one, yes.

Mdadm sometimes does magical things, but if two drives failed, and at the same time, thereby giving spares no chance to take over, the data can't be intact anymore.
Are you sure a spare didn't sync?

If not, I can't say for sure why it appeared to be clean. Maybe some parts of the filesystem where cached, maybe strange behavior of linux. Or maybe there's missing information and two drives didn't fail at the same time.

One thing for sure is to say: An array with that much members should not be raid 5. Splitting it in two and using LVM (not really my specialty) is a better idea. Or even raid 6 if two spares where available.

In situations like this, the least we need to have to help is the examined output of the array members.

```

mdadm --examine /dev/sd[b-m]1

```


Now you post the second post...:
That's sound quite possible. The spare probably wasn't finished, thereby leaving some parts of the data usable, and the other part completely unrecoverable. Not something the filesystem expects, so that may have cause the fsck.

---

