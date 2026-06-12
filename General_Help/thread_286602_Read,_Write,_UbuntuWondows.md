---
title: "Read, Write, Ubuntu/Wondows"
date: 2006-10-28
forum: General Help
---

### Post by Uncle Spellbinder on 2006-10-28
Well, I've got 125 Gigs left on my HD (25 Gigs for Windows, 20 Gigs for Ubuntu Edgy, 125 Gigs unallocated space).

I'd like to create a partition in which I can fully share (read *and* write) between Ubuntu and Windows. Is this possible? If so, I have a Gparted CD, what should I format it to?

---

### Post by magicfab on 2006-10-28
I would personally use ReiserFS or ext3. FAT32 is nice but at such sizes I have always had problems. I know there are Windows drivers to read both ReiserFS and ext3, but haven't had to rely important data on them. I would say:
1) Backup,. backup, backup
2) Make a few tests with smaller partitions, unmportant data
3) Make your install *earn* your trust :)

By all means, if you decide to experiment ReiserFS or ext3 under Windows, come back and report your results here.

Good Luck.

---

### Post by Uncle Spellbinder on 2006-10-28
I created an ext2 partition in Windows using [fs-driver](http://www.fs-driver.org/). No problem writing to it in Wondows. Several notepad files, copied a few .mp3's and a backup of my Windows Minefield (Firefox) profile. Rebooted to Edgy, I don't see the partition. How do I view it. I suppose I have to manually mount it?

---

### Post by hearnden on 2006-10-28
You'll have to manually add an entry to /etc/fstab for your new partition.  You just need

[LIST]
[*]a mount point; and
[*]the device name for your partition (e.g. /dev/sda5)
[/LIST]

By looking at the other entries in /etc/fstab and a quick reading of the 'mount' man page, you should be on the right track.

I'd also agree that using an ext2/3 filesystem for sharing data between Linux and Windows is probably the better alternative; I've never had any trouble with it.

---

### Post by Uncle Spellbinder on 2006-10-28
I'm not sure how to go about this at all. I've not had to manually mount before. I did find some info using forum search...a bit confusing (to me anyway). Anyone willing to guide me please?

The new *ext2* partition is */dev/sda4*

My */etc/fstab*
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=45540423-4339-477f-ba9a-f5c54cfc0b62 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=e07fe74a-404c-4c4f-9f00-977496d4375e none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by hearnden on 2006-10-28
First create a mount point where you want to access files on that partition.  For example, /mnt/windows or /shared or something.

```

$ sudo mkdir /shared

```

Then try to mount the partition manually, with something like:

```

$ sudo mount -t ext2 /dev/sda4 /shared

```

If that all works, then you can add that information to the FileSystem TABle (/etc/fstab), something like:

```

/dev/sda4    /shared      ext2   defaults   0     2

```

Then you should be able to mount the partition by just using:

```

$ sudo mount /shared

```

The only thing that you might want to change is the set of mount options (the 'defaults' part), depending on whether or not you want that partition to be automatically mount when you boot, accessible by all users or just some, etc. etc.  Then you can replace 'defaults' with something like 'noauto,user'.  See the man page for mount for a complete list of the many options you can give.

I'm a dapper user, so I'm not sure why the edgy upgrade has replaced the device names with UUIDs for your other entries in /etc/fstab, so you may need to investigate.

Hope that helps.

---

### Post by Uncle Spellbinder on 2006-10-28
@ hearnden

Thanks. As I'm the only user, I'd like it to automount. I'll investigate further after work (sneaking a peak at the forums at work). ;)

---

