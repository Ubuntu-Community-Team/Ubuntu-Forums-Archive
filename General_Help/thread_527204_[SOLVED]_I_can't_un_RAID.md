---
title: "[SOLVED] I can't un RAID"
date: 2007-08-16
forum: General Help
---

### Post by azelter on 2007-08-16
I have been using RAID for a couple of years on 2X200GB devices (/dev/hdc and /dev/hdd). Now I decided I wanted to use them as "normal" devices as I am running out of space. If I boot into a live system I can mount and read either disk. Therefore, I booted into feisty live and used fdisk to make /dev/hdd1 covering the whole disk. I marked this as partition type 83 (linux) and did mkfs.ext3 on the device. I then copied the contents of /dev/hdc onto it (which is of course what was there before anyway). I then used fdisk to make dev/hdc1, again, covering the whole disk. This file I formated as ext3 but left the disk blank.
I then edited my fstab so the the appropriate line no longer referred to /dev/md0 but to /dev/hdd1 and rebooted.
My problem is that when I rebooted, my system still assembles /dev/hdc and /dev/hdd into RAID array /dev/md0 automatically despite the fact that I made new, non-RAID partitions on them.
I have a feeling it is because I originally issued the devices as /dev/hdc and /dev/hdd without further partitioning the disks, so there must still be some flag left on the disks saying "I'm a RAID disk - assemble me". However, using gparted or fdisk, I cannot find and cancel this.
I'd be very glad on advice on how I can unRAID these disks!
Thanks in advance.

---

### Post by fjgaude on 2007-08-16
Install mdadm from Synaptic if you haven't already. Then do:

```
sudo mdadm --stop /dev/md0
```

Such must be done from a liveCD or from a running partiton; the array can't be currently in use, running. Then your disks will be free to do as will with them.

frank

---

### Post by azelter on 2007-08-16
Thank you very much.
So where is the tag on the disk stored that says they are raid, even after I have fdisked both disks?

---

### Post by azelter on 2007-08-16
Also, the live CD doesn't assemble the disks to /dev/md0 so wouldn't your command produce an error as /dev/md0 probably will not exist (I'm not sitting in front of the machine right now)?

---

### Post by fjgaude on 2007-08-16
Okay, I see your issue... I usually have the OS on a non-RAID partition so I can do what needs to be done to RAID which is not running.

The only way I know of to release the resources of an array is the way I stated. You see the kernel since about 2.6.16 has knowledge of md as it comes up, so an /dev/mdx is there to have it worked upon even though it is not mounted.

Try this: boot however you can, then use mdadm to release the drives from the array, even if it means setting the drives back to auto raid or whatever.

frank

---

### Post by azelter on 2007-08-16
Frank,
Thanks very much. I have been reading based on your advice and the situation is as easy as you first suggested. I was just confused by the liveCD aspect. My root is not raid so I'm ok there. I'm just a little scared as I made all the changes I first described (i.e. reformatting one array as a blank ext3 and then copying from the other device to that and then reformatting the other device). So now when I boot up it reassembles the raid array - very scary, as it will presumably trash all my data trying to sync the disks. Thus I think I need to do the following:
1/ unplug power from hdd (which I hope still has my data)
2/ fire up in machine normally - it should start raid with one device (hdc - which will be empty as I formatted it)
3/ stop the device and zero superblocks (reading tells me this is the key command [mdadm --zero-superblock /dev/hdc])
4/ shutdown and plug in hdd reboot in livecd and (fingers crossed) reformat hdc and copy contents of hdd to hdc1 (having made a new ext3 fs on it) and edit fstab so filesystem that md0 was mounted to now mounts hdc1
5/ unplug hdd again and check system boots normally without trying to start raid and that all is there in hdc1
6/ if all is well unplug hdc and plug in hdd and reboot in after booting normally - RAID will try to start hdd as this still has the RAID superblocks. Remove hdd from raid array and zero superblocks, format as ext3 and reboot to check it's no longer assembled into raid
7/ shutdown and plug in hdc (so both are now plugged in and reboot to check both are now happy and unraided and not trying to sync each other.

Fingers crossed this works and the few seconds that the RAID arrays were assembled post my messing around did not result in major data loss...

---

### Post by fjgaude on 2007-08-16
Very good, and now is the time to post [SOLVED] under "Thread Tools" for this issue.

frank

---

### Post by azelter on 2007-08-16
Well, I guess I'll try it first ;-) ...

---

### Post by fjgaude on 2007-08-16
I got the impression that you were already running it. Sorry about jumping the line...

frank

---

### Post by azelter on 2007-08-16
OK - now I am freaking out. Here is what I have done so far from the beginning:

- I had 2 drives in raid array (hdc & hdd)
- I booted into feisty live and used fdisk to make /dev/hdd1 covering the whole disk. I marked this as partition type 83 (linux) and did mkfs.ext3 on the device. 
- I then copied the contents of /dev/hdc onto it (which is of course what was there before anyway). I then used fdisk to make dev/hdc1, again, covering the whole disk. This file I formatted as ext3 but left the disk blank.
- when I rebooted, my system assembled /dev/hdc and /dev/hdd into RAID array /dev/md0 automatically despite the fact that I made new, non-RAID partitions on them.
- as soon as I saw this (less than 1 minute uptime) I shutdown

then later ...

- I unplugged hdc and booted up. Machine started md0 using hdd only as that was all that was there
- I did: mdadm --stop /dev/md0 (no problem there, raid is down as desired)
- I then did: mdadm --zero-superblock /dev/hdd (ok)
- I then try: "mount -t ext3 /dev/hdd /data" but I get a bad superblock error and the filesystem can't be mounted
- I then boot into live Feisty CD and successfully mount: /dev/hdc to /home/ubuntu/hdc and /dev/hdd1 to /home/ubuntu/hdd1

The thing is - ALL MY DATA SEEMS TO BE THERE ON BOTH DISKS!!!

But I fdisked /dev/hdc and made /dev/hdc1 and did mkfs.ext3 on it. And there is no way it mirrored all that data back in under a minute (it took a couple of hours to copy it from /dev/hdc to /dev/hdd1 in the first place). Also RAID is not running on the live CD. 

du gives the same disk usage for both disks.

So now I am scared to do anything as I don't know what's going on and where my data really is.

Ideas as to how this could happen?

I think I'll plug in an external drive and copy my data somewhere else ...

---

### Post by fjgaude on 2007-08-16
I'm about out of ideas, other than to say that when you do mkfs -t ext3 on a disk that has already had a ext3 on it and was "erased", really there's likely one byte that got changed to released the whole disk filesystem. I remember one time I deleted the whole filesystem and then did something like a mkfs.ext3 and I had everything back as it was. No data got removed or lost, and I wanted it all to go away and start fresh.

Other than copying all your data onto another disk as you suggest, and then re-install the OS on one of the present disks that's about it. Of course you could start writing new stuff to one of the disk, the one that you wish to start over with and see what happens.

Good disking,

frank

---

### Post by azelter on 2007-08-17
So the simple answer for my system in the first place would have been to do:
sudo mdadm --stop /dev/md0
sudo mdadm --zero-superblock /dev/hdc
sudo mdadm --zero-superblock /dev/hdd
This would have unraided my disks - as I'm sure any RAID expert would know.
I've managed to recover from all the weirdness and now have my 2 ex-RAID disks running LVM with all their original data on them but twice the space and no redundancy.
Thanks for all the comments.

---

### Post by fjgaude on 2007-08-17
Happy you have the issues solved.

I must say that I have released many disks from arrays before and never did a zero-superblock on them. I did put in new filesystems using Gparted or the like and went my merry way. So...

Great news to be able to move forward.

frank

---

