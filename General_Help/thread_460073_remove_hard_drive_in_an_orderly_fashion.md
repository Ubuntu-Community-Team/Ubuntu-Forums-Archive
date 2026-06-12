---
title: "remove hard drive in an orderly fashion?"
date: 2007-05-31
forum: General Help
---

### Post by linuxgrrl on 2007-05-31
hi,
my exhaust fan died, causing heat damage to (at least) one of my hard drives.  Trying to dig out of this mess now.

I was able to copy the files off the damaged drive, thank goodness, now it's time to get rid of the offending drive.  What Ubuntu settings, if any, must I change when I do this?

I should mention I have LVM installed.  My / is on a regular (non-lvm) partition and all my photos, music, etc. are stored under LVM partitions.  I have already removed the offending drive from my LVM setup using the command "vgreduce" and the excellent instructions in the LVM howto.  

My question is, what to do next? The removed drive was /dev/hdb ... if I just (physically) remove it now, will it cause Ubuntu to re-designate /hdc and /hdd with different names?  Will that cause mass confusion for the file system?

Sorry for not just experimenting with it, but frankly I'm afraied /dev/hda may have been damaged too so I don't want to play around too much with rebooting, etc. before that one kicks the bucket as well.  Replacing /dev/hdb with a new drive (to preserve the mapping order)  is also not an option ... I think that all the messy cabling, too many drives crowded in, etc. contributed to my heat problem in the first place.
thanks for any advice.

---

