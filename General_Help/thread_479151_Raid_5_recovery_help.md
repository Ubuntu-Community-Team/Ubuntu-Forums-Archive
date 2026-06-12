---
title: "Raid 5 recovery help"
date: 2007-06-20
forum: General Help
---

### Post by markljames on 2007-06-20
I have a RAID 5 setup with 4 disks.  Since the disks were all purchased at the same time, I planned to replace them one by one over a few months.

I removed the first disk and installed a replacement.  I added the new disk and mdadm showed the raid recovering and rebuilding onto the new drive.

About 1/2 way through this operation, one of the other drives failed.  It gets I/O errors part way through the recovery and it gets marked as failed.

I can boot and see the raid array fine, but I can't recover it properly with one of the disks failing.

I have the original disk.  Is there some way I can put it back and get a functioning array and remove the faulty drive?

Thanks.

---

### Post by bunker on 2007-06-20
A two-disk failure usually means your entire array is gone, I'm afraid.  If possible, get one of the disks working again and do a normal recovery - if it's not a mechanical failure, you can often do this by replacing the circuit board with one of exactly the same type (including firmware).  Other than that, you could try the steps [here](http://tldp.org/HOWTO/Software-RAID-HOWTO-8.html#ss8.1), but there's a good chance you'll loose all the data anyway.

---

### Post by markljames on 2007-06-20
Thanks for the suggestion.

The thing is, the first disk didn't fail.  I just removed it to replace it with a newer disk.

I'm trying to figure out how to put it back and recover the array.

It seems that mdamd --assemble does what I want, but the disks are being auto detected on boot, so it won't let me change the array.

     M.

---

### Post by peachy on 2007-06-26
hi there, re-connect the "good" disk you removed then:
sudo mdadm --re-add /dev/md0 /dev/sdf

where /dev/md0 is your raid array and /dev/sdf is the disk you re-added. 

You should have working, degraded raid array then and will be ready to rebuild disk 4.

---

