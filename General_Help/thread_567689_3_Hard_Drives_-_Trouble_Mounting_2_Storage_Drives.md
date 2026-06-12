---
title: "3 Hard Drives - Trouble Mounting 2 Storage Drives"
date: 2007-10-04
forum: General Help
---

### Post by tusamni on 2007-10-04
Just switched over to Ubuntu about two weeks ago.  I am really enjoying it :)

I have my main hard drive (36GB Raptor) mounted and running fine.  I have two other internal drives which are my storage drives.  I am having trouble getting them to run perfectly.  I have one mounted, but it doesn't seem right.  I need to enter my password to get to it everytime I start up the computer and it doesn't look like it's mounted the same as my boot drive in the Computer screen.

Here is some information you'll probably need to see:

**BLKID**
```
/dev/sda1: UUID="518a3e4f-19cd-4a0f-8dd1-1f0b1bc35a88" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="457b1a1b-1ed6-414c-9e6e-f82408550f9f" TYPE="swap" 
/dev/sdb1: TYPE="ntfs"
```

**SUDO FDISK -LU**
```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    69240149    34620043+  83  Linux
/dev/sda2        69240150    72292499     1526175    5  Extended
/dev/sda5        69240213    72292499     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
```

I've been using this tutorial to help me: [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

It got me pretty close, but again, my drives don't automatically mount up when Ubuntu starts.  And they still are saying NTFS when using the BLKID command?

I probably left some things out, so let me know what I can provide to solve my problems!

Thanks,
-Erik

---

### Post by tusamni on 2007-10-04
Nevermind, I read more of that tutorial I posted and it showed how to edit the etc/fstab to mount the drives on bootup.

All set now! :)

---

### Post by at a loss on 2007-11-01
Can you still write to them though?  I got my 2 to mount on startup with 7.10 but I can't use them.

---

### Post by taurus on 2007-11-01
> **at a loss said:**
> Can you still write to them though?  I got my 2 to mount on startup with 7.10 but I can't use them.

What filesystems are those two partitions and where do you mount them?

Post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by at a loss on 2007-11-02
I seem to have got them working using the 'how to' link above.  I still don't understand why linux does this, it's an awkward problem for new linux users like myself.  If I get anymore problems I will come back.  :)

---

