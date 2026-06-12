---
title: "DMRAID - possible to grow RAID5?"
date: 2013-06-11
forum: General Help
---

### Post by LoungeLizard on 2013-06-11
I know with mdadm RAID scenarios, I can fail and replace / add drives to a RAID5 array and rebuild the array.  I also know that I can increase the size of my array "somewhat" in a non-trivial pursuit with MDADM (not a task for the feint of heart, IMHO)....  

But, I have a challenge!  I have a scenario with a 'media' server having a DMRAID setup where the RAID5 array was originally configured using DMRAID with an nvidia driver through the MOBO and the RAID5 volume is not used for booting and is mounted as /data - "a data drive".  Let's say I have inherited a machine with a 4-disk RAID5 using 360GB drives and I happen to have 4 2TB disks.  The challenge: I want to replace all four drives - but I want to do it piecemeal, replacing one at a time and rebuilding the array (hopefully not losing any data).  Then after the fourth replacement, I want to grow the filesystem to maximize the unused space.  Is this even possible with DMRAID?  

My research so far is not revealing how to fail a drive and remove it from an existing array and replacing it.  My first attempt was 'a simple WTF, just replace one of the drives and see what happens'.  Upon boot, I get a failure that the mount point cannot be mounted: > nvidia:wrong # of devices in RAID set "nvidia_aafjfffa" [3/4] on /dev/sd[bde] and ultimately it is considered 'inconsistent'.  Of course, it is inconsistent - apparently I removed the drive that was /dev/sdc...  Checking in palimpsest shows that my replacement 2TB drive is identified as /dev/sdc and is completely new and uninitialized.

So, I try to force a rebuild anyway thinking maybe DMRAID is smart enough to just do it without me having to prepare the new drive (since I'm not finding anything in the man pages or in my various google searches on the specific procedure): ```
sudo dmraid -R nvidia_aafjfffa /dev/sdc
```
> ERROR: nvidia:wrong # of devices in RAID set "nvidia_aafjfffa" [3/4] on /dev/sd[bde]
ERROR: removing inconsistent RAID set "nvidia_aafjfffa"
ERROR: no RAID set found

So, putting the old drive back forces a fsck and recovers the journal from /dev/mapper/nvidia_aafjfffa1 and I let it go through and completely check the drive since this fileserver has been running for a couple of years in its original configuration. When it reboots completely, everything is peachy...  I don't have a backup of the media data on the drive (well, all the really important stuff is backed up to a file server) - it's not that important, just that it's a lot of stuff (nearly a TB of media files) and I'd rather not lose it or have to re-create it - I just want more space.  Adding more drives is not a desired option - even though I have room (this is a tower case), I don't have the desire to increase my power supply capacity nor my carbon footprint nor do I want to buy another drive controller card. My MOBO is already maxxed out on it's capacity number of drives - heck I even have two slots I can't fill because of not enough drive ports on my mobo.

I digress...  I suppose what I need to do is unmount the /data drive (this is the mountpoint of the RAID volume) and determine a better way...

Further research on this issue is not revealing how to "properly" fail a DMRAID drive and remove it from a DMRAID configured RAID5 array.  Nor have I found a means to add a new drive and rebuild an inconsistent array.  Anyone successfully doing something like this?  Any suggestions?

Perhaps I can find a means to convert the DM RAID to an MD RAID - but the couple of threads on that topic I found don't hold anything promising...

-- da Lizard

---

