---
title: "Mounting a windows XP spanned drive"
date: 2008-04-23
forum: General Help
---

### Post by frootloop on 2008-04-23
Hi,

I've been searching for a solution to this one for a while now, with no luck. I hope someone here can point me in the right direction! 

I have Ubuntu installed on a ext3 partition on my previously windows only system. My problem is that my windows data partition is a spanned volume that is spread across 3x250Gb drives and one 320Gb. Ubuntu did not recognise this volume during install. Post install, Ubuntu shows the volume in nautilus with the correct windows drive letter and label, but I cannot access the volume.

The closest I got to a solution is this post:
[http://forum.linux-ntfs.org/viewtopic.php?p=1572&sid=7e2ba87c68c9e2416cf6cc27aa2bca75](http://forum.linux-ntfs.org/viewtopic.php?p=1572&sid=7e2ba87c68c9e2416cf6cc27aa2bca75)

I just dont understand how to implement what is suggested! From my tinkering, I think my standard Gutsy kernal has LVM enabled, which is why I am seeing the window drive letter and label - I'm stumped so far on how to 'paste all the drives together using software RAID'

Any help would be appreciated! I'd really like to access my Data partition through Ubuntu and trash windows completely.

I cannot simply delete the windows LDM and creat  a Linux one - I dont have the space to back up the contents of the drives first!

Regards

---

### Post by chrisccoulson on 2008-04-23
When you are referring to a 'spanned' volume, are you suggesting a setup like RAID0? If so, then I might be able to help you out.

The reason you see the volume in Nautilus is because the kernel sees several disks, and one of them has a valid partition table - so it exposes the 'partitions' in /dev, but the partitions are actually invalid and cannot be accessed.

---

### Post by frootloop on 2008-04-23
Hi there, i'm not quite sure what you are asking? The setup under windows is more akin to software JBOD than RAID. Essentially one logical volume is spanned accross multiple physical drives, so you end up with one large logical drive exposed to windows, but with no redundency etc. Is that waht you meant?

---

### Post by frootloop on 2008-04-23
Okay, I think I know what you mean now - its a linear raid setup.
I think I may have figured out how this works, going to try tonight and post results  back here :)

---

### Post by Smurph on 2008-06-09
Success!!

I manged to mount a windows ntfs volume spanned over two disks!  I'm running ubuntu hardy.

I followed the guide at:
[http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)

Particularly the section titled "The Device-Mapper driver"

Some important notes though (problems I had and how I solved them)

- Before you can use dmsetup you need to do this:

    $ sudo modprobe dm_mod

Otherwise you get a compatibility error, which should be a permission error.  The wrong error is displayed because of a bug.

- The command:

    $ sudo mount -t ntfs -o ro /dev/device-mapper/myvolume1 /mnt/myvol1

Returned an error, not found. I found it needed to be:

    $ sudo mount -t ntfs -o ro /dev/mapper/myvolume1 /mnt/myvol1

It may be different for you.

I'm a linux newbie but thats what I did and it seemed to work.  Hope it helps!

---

### Post by frootloop on 2008-06-09
Kudos Smurph! Been meaning ot post my solution, but studies have been keeping me busy:( Thanks for posting the solution!

---

### Post by davemarker on 2010-05-14
Sorry to dig this one out of the archives, so to speak, but I'm having a similar problem. I have a buddy of mine who's turned to me for help with an external drive set. Here's where I'm at right now.  I've got two sata drives plugged into a machine and I'm booting into an ubuntu 10.04 liveCD session.  ubuntu sees both the drives, sdb and sda. Both are 500GB drives. sdb has a 1TB fat32 partition on it, sdb1, and sda is listed as unformatted.  I can mount the partition and copy some files, but many of them are generating read errors.

The impression I'm getting here is that it's a spanned disk/linear raid setup.  I've read through the ntfs.txt walkthrough listed here and it's talking about joining together two partitions for the linear raid.  There's only one partition listed in my situation, so I'm not sure what to do from here.  Can anyone help me out here?

---

