---
title: "clone a windows partition from live usb?"
date: 2014-04-07
forum: General Help
---

### Post by sdowney717 on 2014-04-07
Anyone can share a good way to do this?
One that preserves boot for windows 7.
Windows 7 install disc does have a fixboot feature.
Windows 7 also has a 100mb system partition which you dont have to have, 
windows 7 creates one on a fresh install that hold boot files for the main partition.

I have a 60gb I want to clone onto an 80gb.
Plan is to keep the 80gb as a backup for the 60gb so when the 60gb gets malware infected and otherwise corrupted,
I can clone back onto it from the 80gb backup.

I want to do this from a liveusb without windows getting involved because the 80gb might be infested.

Maybe clonezilla?

---

### Post by sdowney717 on 2014-04-07
running clonezilla nice program, if it simply boots without having to fixmbr will be nice.
I selectd disk to disk copy and also clonezilla asked about a boot loader and I said yes also.
I will boot the clone just to see if I got a good copy.

---

### Post by sdowney717 on 2014-04-07
very nice, clonezilla worked duplicating the drive, it booted up with no problem.
[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)
I downloaded the iso file i686 stable and used unetbootin to make the live usb.

---

### Post by Double.J on 2014-04-07
Hi there!


The most accurate way to copy one disk to another is with the dd command as it will literally copy block by block from one to the other preserving everything. The downside is that it takes AGES because it will even copy the free space - it doesn't care what's there, it just copies copies copies.

User friendly is probably still clonezilla - set it to clone disk. 

A bit more work but a bit quicker, is ntfsclone. you still have to dd the mbr, but ntfsclone is a lot faster. [This guide]("http://www.nilbus.com/linux/disk-copy.php") is pretty old now, but the commands are still valid so long as you aren't using UEFI and/or GPT 

I tend to just dd my drives and walk away and come back a lot later. 

```
sudo dd if=/dev/oldhhd of=/dev/newhdd conv=noerror,sync
```

Of course Back everything up first, and make triple sure that the hard drive you are copying from is after 'if' (input) and the drive you are going to totally erase and replace if after the 'of' (output)

Which ever method you use be continuously certain which drive is being copied and which is being writen. If you aren't sure, don't hit go until you are. Also remove all othe media from the machine - external hard drives, memory cards, smartphones that are charging, heck even the last reamining floppy. Whichever cloning technique you use it'd curtains for the drive you write on to, so make usre it can't be anything other than the one you want erased.

Jj
Edit - Ha! I must have started replyingjust before you posted! Glad it all went without a hitch! :D

---

### Post by sdowney717 on 2014-04-07
yes, worked well.
I have to see what it did about free space since drives are different sizes.

I had been thinking I had malware infection that maybe was not detectable so tried a new install. And when the new install worked with no HDTV streaming glitches ( I use this as a HTPC), I thought I should clone the drive for a backup.

If it works for a few days, then maybe was either corrupted files or malware.
So now, I have a known good backup clone.

---

### Post by Double.J on 2014-04-07
It's been a while since UIused clonezilla but I believe it just creates the oringinal partitions on the new drive (so that you would have ~20GB free space at the end. windows tools should be used to close this up) if it's changed please let me know!

I know the relieve of having a Backup clone - I have 2TB drive that has maybe 15/20 backup image files on it now!

---

### Post by sdowney717 on 2014-04-07
> **gnu/mirow said:**
> It's been a while since UIused clonezilla but I believe it just creates the oringinal partitions on the new drive (so that you would have ~20GB free space at the end. windows tools should be used to close this up) if it's changed please let me know!

I know the relieve of having a Backup clone - I have 2TB drive that has maybe 15/20 backup image files on it now!

I wonder, what would happen If I cloned the 80gb partition, if I expanded it using windows tools,  (with plenty of free space), back onto the 60gb drive?

---

