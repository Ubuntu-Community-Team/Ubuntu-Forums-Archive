---
title: "How to move a software RAID to another machine?"
date: 2008-07-05
forum: General Help
---

### Post by SupaRice on 2008-07-05
So I have two computers, my old one and my new one.  The old one has two 250GB drives that I had setup into a software RAID 0 when I installed Ubuntu on it many moons ago.  How can I set those up in the new machine, which already has Ubuntu installed on it without loosing any of the data?  I'd like to mount then as like /storage or something.

---

### Post by fjgaude on 2008-07-05
I've had no troubles moving mdadm raid arrays from one machine to another. On the new machine simply plug the drives into the SATA slots, order makes no difference. Then boot, install mdadm and then:

```
sudo mdadm --assemble --scan
```

And the array comes up. Now mount in the usual manner using the /dev/md[n] name, into the fstab file also.

Let us know if you have issues. No matter what, **do not** do a **--build** or **--create**. For sure all data is loss then.

---

### Post by SupaRice on 2008-07-05
> **fjgaude said:**
> I've had no troubles moving mdadm raid arrays from one machine to another. On the new machine simply plug the drives into the SATA slots, order makes no difference. Then boot, install mdadm and then:

```
sudo mdadm --assemble --scan
```

And the array comes up. Now mount in the usual manner using the /dev/md[n] name, into the fstab file also.

Let us know if you have issues. No matter what, **do not** do a **--build** or **--create**. For sure all data is loss then.

Wow, that's WAY easier than I thought it'd be.  I'll give it a shot tomorrow and let you know how it goes.

---

### Post by uhclay on 2008-07-29
Well, how did it go?

---

### Post by prince_of_hackers on 2008-07-31
Maybe someone in this thread can help me - I built a RAID 5 array using six SCSI disks, formatted and mounted it - works great until I reboot, and then four of the disks no longer have a partition table and the array cannot be assembled - any ideas?

The RAID superblocks seem to be fine, if I create a new disklabel and partition it EXACTLY the same as it was before, it will assemble and work just fine, until the next reboot...

---

### Post by SupaRice on 2008-07-31
Worked like a champ!  Sorry for the late reply, and thanks for the help. 

:guitar:

---

### Post by SupaRice on 2008-07-31
> **prince_of_hackers said:**
> Maybe someone in this thread can help me - I built a RAID 5 array using six SCSI disks, formatted and mounted it - works great until I reboot, and then four of the disks no longer have a partition table and the array cannot be assembled - any ideas?

The RAID superblocks seem to be fine, if I create a new disklabel and partition it EXACTLY the same as it was before, it will assemble and work just fine, until the next reboot...

Are you referencing them from UUID?

---

### Post by prince_of_hackers on 2008-08-02
Yes - although detection doesn't seem to be the problem. The kernel detects the array from the persistant superblock on the first hard drive, but because the rest of the RAID partitions are gone, it can't find them to assemble the array.

---

### Post by prince_of_hackers on 2008-08-06
OK, I figured it out - unlike a regular ext filesystem, software raid will overwrite the disklabel at the beginning of the hard disks. To fix this, I started the partitions used as elements of the raid array on cylinder one instead of the default cylinder zero, and everything seems to work great now.

---

### Post by rorona on 2008-09-30
I have a similar situation where I am moving my raid to newly OSed harddrive, but I have a logical volume defined with my raid. I originally built my raid 5 by following the procedures from the following site: [http://starnixhacks.blogspot.com/2008/04/ubuntu-lvm-on-software-raid.html]("http://starnixhacks.blogspot.com/2008/04/ubuntu-lvm-on-software-raid.html"). I used the assemble and scan option of mdadm, and that seemed fine. I have /dev/md0 now. Now I'm just missing /dev/volgroup00/logvol00 to mount to /mnt/data. Do I need to export the volume first, so I can import it using vgimport? I would appreciate any help. Thanks in advance. :)

---

### Post by rorona on 2008-09-30
Ok, I managed to find the answer myself through the magic of Google and reading threads on just generic Linux.

In hopes that this might be helpful to someone else, I will try to summarize the problem and solution (at least for me). 

I had my boot drive (/dev/sda1) fail on my server where I had a software Raid 5 array (/dev/sdb1, /dev/sdc1, /dev/sdd1) configured with a logical volume. I purchased a new drive which I OSed, and I wanted to move my raid array in a non-destructive manner onto the new boot drive. So, I found a number of references (including this one) that recommended doing a "sudo mdadm --assemble --scan". This helped the OS to recognize my array, but I couldn't mount my logical volume. LVM was able to see I had a logical volume though. I found the the missing step was to do a "sudo lvchange -ay volgroup00". After that, my logical volume appeared under /dev, and I was able to perform "sudo mount /dev/volgroup00/logvol00 /mnt/data". BTW, I found the step at the following link: [http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem").

I hope this info is useful to someone else in the future.

Thanks.

---

