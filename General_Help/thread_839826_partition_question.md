---
title: "partition question"
date: 2008-06-24
forum: General Help
---

### Post by raichle on 2008-06-24
Hi all and thanks in advance. 

I am dual-booting 8.04 and Vista and each have a ~125 GB partition.  Is there any safe way to repartition so that each only has 50GB and there is 100 GB formatted as NTFS or Fat32 so it's available to both?  I have no data on this computer yet as these are both new installs.

---

### Post by raichle on 2008-06-24
Incidentally, I followed the steps here to initially install both OS's:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by jeremy1138 on 2008-06-24
gparted can resize partitions I believe...  Can anyone confirm this for me?

---

### Post by klytu on 2008-06-24
> **raichle said:**
> Hi all and thanks in advance. 

I am dual-booting 8.04 and Vista and each have a ~125 GB partition.  Is there any safe way to repartition so that each only has 50GB and there is 100 GB formatted as NTFS or Fat32 so it's available to both?  I have no data on this computer yet as these are both new installs.

I would recommend that you use Vista's native partioning tool to shrink Vista's partition down to 50GB and set up a separate 100GB NTFS partition. Leave the rest of the drive as free space. Next reinstall Ubuntu on 50GB of the remaining free space. There may be other ways to accomplish your goal, but in my opinion this would be the easiest and safest way.

---

### Post by raichle on 2008-06-24
I'd really like a way where I don't have to reinstall Ubuntu.  I finally got everything installed and setup the way that I like it...

---

### Post by louieb on 2008-06-24
> **raichle said:**
> ...got everything installed and setup the way that I like it....


[LIST=1]
[*]use partimage to backup your Ubuntu partition.
[*]shrink you Ubuntu partition to size you want it.
[*]Makes sure it still works after being shrunk.
[*]Then use partimage to make a 2nd backup.
[*]Delete you old Ubuntu partition.
[*]Create  your new partitions.
[*]restore the Ubuntu partition from the 2nd  partimage backup.
[*]reinstall GRUB.
[/LIST]
Lots of ways to do it. The above is a reasonably safe way.  One thing about restoring from a partimage backup the partition must be the same size or larger that the original partition thats the reason you need the 2nd backup.

---

### Post by raichle on 2008-06-24
Couldn't I just shrink the vista partition using vista's built-in tool and then use gparted or something like that to shrink the linux partition?  

The partimage directions sound really complicated...

---

### Post by VMC on 2008-06-24
> **raichle said:**
> Couldn't I just shrink the vista partition using vista's built-in tool and then use gparted or something like that to shrink the linux partition?  

The partimage directions sound really complicated...

You could do that, but where is Swap at in the mix. The end middle, or extended?
Maybe an fdisk output would help. Also be aware of Grub not working until you re-align the partitions. Then your UUID's will change, but that's no dig deal.
Lets start from Terminal:

```
sudo fdisk -l
```

---

### Post by raichle on 2008-06-24
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15654   125737792+   7  HPFS/NTFS
/dev/sda2           15655       30401   118455277+   5  Extended
/dev/sda5           15655       29796   113595583+  83  Linux
/dev/sda6           29797       30401     4859631   82  Linux swap / Solaris

---

