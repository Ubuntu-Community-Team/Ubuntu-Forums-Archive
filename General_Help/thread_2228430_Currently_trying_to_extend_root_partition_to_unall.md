---
title: "Currently trying to extend root partition to unallocated, but can't find option."
date: 2014-06-07
forum: General Help
---

### Post by Mike1977 on 2014-06-07
So my install created a 16 GB linux-swap partition to match my RAM. I am in the middle of shrinking that swap partition to 2.5 Gib (GB?) and am trying to eat up the unallocated space by extending the 41.28GB root. However, when I click "resize/move" on EXT4, I'm not seeing the option to extend. Is it because I haven't commited to the shrink on swap yet? What am I missing?

---

### Post by LastDino on 2014-06-07
Probably yes, but this moving right thing takes considerable time, so stay prepared.

---

### Post by Mike1977 on 2014-06-07
> **LastDino said:**
> Probably yes, but this moving right thing takes considerable time, so stay prepared.
Looking at my screenshot, Do I have it qued correctly? Before I commit to " Move /dev/sda6 to the right and shrink it from 15.94 Gib to 2.52 Gib", I want to make sure that I will then be able to extend sda1 to unallocated spac without anything in the way.

---

### Post by LastDino on 2014-06-07
Problem with your set-up is that your swap is in extended partition, I've never worked with this set-up but my assumption is that you probably wont be able to add that area to Root even if you did move it to wherever you're moving it right now. 

As Qlll, has suggested in your other thread, you might get rid of the swap all together here, or keep that remaining unallocated space where it is and maybe sometime in future, use it for testing some other Linux distro by installing it on there.

Nevertheless, to avoid making things complicated, and assuming Linux is the only OS on your HD, forget about adding this to your Root. You can use that extended partition for storage as Linux can read WIndows partitions as well. 
One question though, why is it in fat? and is there any other OS on it?

---

### Post by Mike1977 on 2014-06-07
> **LastDino said:**
> 
One question though, why is it in fat? and is there any other OS on it?

Yes, I have Windows 7 on a seperate SSD. So I can access TB drive through both OS's. 
I moved ahead and shrank the swap partition to 2.52 GiB. I now have it qued to
 " Move / dev/sda2 to the right and shrink it from 890.23 to 876.81 Gib"
Which then allows me to:
"Grow /dev sda1 from 41.28 GiB to 54.70 Gib" 
which will leave me with 1.00 MiB unallocated that sits to the right of ext4 (part of sda1) * See screenshot* I guess that's par for the course, because I can't seem to actually get rid of that 1.00 MiB unallocated by stretching further.
I'm sure you guys are right. I could just delete the swap partition, but I've already moved forward in this direction. So I guess I'll go this route.

---

### Post by grahammechanical on 2014-06-07
After the swap partition has been resized you then have to shrink the Extended partition (sda2) to create unallocated space behind sda1 and then expand sda1 to take up the unallocated space. I like to do one Gparted action at a time. Otherwise, it can seem a long wait for all actions to be completed.

---

### Post by Mike1977 on 2014-06-07
Ok thanks everyone for your help. This is what I ended up with for now.

---

### Post by LastDino on 2014-06-07
That should work, now check if that swap is getting mounted after you boot into Ubuntu.

Simple way to check that is to opening gparted and see if there is same ''key'' icon in front of swap partition as there should be one in front of ''/'' partition, after booting into Ubuntu. If it is not there, simply install gparted from software centre.

---

### Post by Mike1977 on 2014-06-10
@LastDino
After a few days, I ran Gparted, and this is what I'm looking at: see screenshot.
Interesting that a little bit of swap partition is actually being used. 
Looks like I'm mounted and locked on all 3 Ubuntu specific partitions.

---

### Post by LastDino on 2014-06-10
You're all good now. Technically speaking only 2 are working, SWAP is basically sub partition of that ''extended'' one and as long as anything under Extended is being used/mounted, extended will be shown like that.

And that 4kib is occupied not because you're using it, its a system reserved space, each drive has some amount depending on its size. You're probably never going to use SWAP unless you run like 10 VMs.

---

