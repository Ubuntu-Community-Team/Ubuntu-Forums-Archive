---
title: "Hard drive assignments changed in Hardy?"
date: 2008-05-14
forum: General Help
---

### Post by Fraoch on 2008-05-14
Upgraded to Hardy last night, and on restarting in the morning, I got a scary fsck error, this is from /var/log/fsck/checkfs:

```
Log of fsck -C3 -R -A -a 
Wed May 14 08:14:26 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hdb1

/dev/hdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/hdb2

/dev/hdb2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sdb1: clean, 44/120832 files, 80108/481948 blocks (check after next mount)
/dev/md0: clean, 219954/4276224 files, 5883893/8550544 blocks
fsck died with exit status 8

Wed May 14 08:14:26 2008
----------------
```

and then I went into the maintenance shell.  However CTRL+D brought me to the desktop, minus those drive partitions - thankfully root is not on that drive.

Seems almost like those two drives are corrupted!  running e2fsck -b 8193 /dev/hdb1 or /dev/hdb2 resulted in the same "The superblock could not be read" error.

Thought I might have to reformat (thank goodness I have the data backed up)  but in "Places" I had "Mount 207.1 GB Media" and "Mount backup" entries.  hdb1 was named "music", the name appears to be gone, but hdb2 was named "backup" and there it is.  I mounted them, they mounted to desktop and operate just fine.

However they are addressed as /dev/sda1 and /dev/sda2 and mounted in /media/backup and /media/disk.  I had set fstab to mount them in /home/backup and /home/music.

Can I reset fstab to mount /dev/sda1 to /home/backup and /dev/sda2 to /home/music as before and be done with it?  This PC will be run headless much of the time and I need these partitions auto-mounted, manual mounting at every boot won't work.

Is it normal for Hardy to address all drives as /sd[abc][123] and all I have to do is reassign the drives or did something much more serious happen here?

Thanks in advance for any help or advice.

---

### Post by chrisccoulson on 2008-05-14
Please post the contents of your /etc/fstab, and also post the output of:
```
sudo blkid
```
It will help people suggest the changes you need to make to your fstab to fix your problem. It does seem like your issues are related to changing device nodes, which is why disks are now identified using UUID in fstab

---

### Post by Fraoch on 2008-05-14
Thanks for the quick response!

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md1        /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=73b01b78-e347-44dd-a495-fcdbb08a4d1f /boot           ext3    defaults        0       2
/dev/md0        /home           ext3    defaults        0       2
# /dev/sda2
UUID=b56d4734-34cd-4f9c-a992-04f6043ee504 pri=1            swap    sw              0       0
# /dev/sdb1
UUID=cd04858f-02d4-4a3f-9ebe-e3fd540b3855 pri=1            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdb1 /home/backup ext3 defaults 0 2
/dev/hdb2 /home/music ext3 defaults 0 2
```

It's complicated by the fact that I'm using mdadm - / and /home are on RAID 0 devices.  Yes, I know that's silly, but it works fine for me.  I can remember fooling around a lot with the cdrom0 drive entry in order to get it to work for RubyRipper, it does work but not because of the changes I made in fstab I believe.  sda1 and sda2 are here and seemed to be added automatically (I know nothing about UUIDs and would never have entered that).  Oddly, they are commented out.  I didn't do that.

/dev/hdb1 and /dev/hdb2 are at the end and I added them manually.  I was thinking of just changing these to /dev/sda1 and /dev/sda2 but with other entries for sda1 and sda2 in fstab, even commented out, this might be improper.

Note I also have a backup USB drive which mirrors these two partitions using rsync but I don't believe USB drives are mounted using fstab.  IIRC the two USB drive partitions mount as sdc1 and sdc2.

sudo blkid:

```
/dev/sda1: UUID="7106b2d0-f606-49b9-93cc-6aeb2cf202da" SEC_TYPE="ext2" TYPE="ext3" LABEL="backup" 
/dev/sda2: UUID="13024ea4-d52a-4e12-b818-6984c23b3c96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="73b01b78-e347-44dd-a495-fcdbb08a4d1f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md1: UUID="abe013bb-1606-4b00-9db1-1ff85d1a0583" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md0: UUID="5573db07-c2ef-422f-ae7b-81c84cbb952e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: TYPE="swap" UUID="b56d4734-34cd-4f9c-a992-04f6043ee504" 
/dev/sdb3: UUID="57082957-be96-3636-025a-3fbd9c418b35" TYPE="mdraid" 
/dev/sdb4: UUID="b2c88fc3-2226-8db8-15f6-8e967253f4e9" TYPE="mdraid" 
/dev/sdc1: TYPE="swap" UUID="cd04858f-02d4-4a3f-9ebe-e3fd540b3855" 
/dev/sdc2: UUID="57082957-be96-3636-025a-3fbd9c418b35" TYPE="mdraid" 
/dev/sdc3: UUID="b2c88fc3-2226-8db8-15f6-8e967253f4e9" TYPE="mdraid" 

```

...which kind of seems to indicate that my USB drive won't mount as sdc1, sdc2 anymore?

---

### Post by chrisccoulson on 2008-05-14
Right, here is how I think your fstab should look. I've also corrected comments (all highlighted in red)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md1        /               ext3    defaults,errors=remount-ro 0       1
[COLOR="Red"]# /dev/sdb1[/COLOR]
UUID=73b01b78-e347-44dd-a495-fcdbb08a4d1f /boot           ext3    defaults        0       2
/dev/md0        /home           ext3    defaults        0       2
[COLOR="Red"]# /dev/sdb2[/COLOR]
UUID=b56d4734-34cd-4f9c-a992-04f6043ee504 pri=1            swap    sw              0       0
[COLOR="Red"]# /dev/sdc1[/COLOR]
UUID=cd04858f-02d4-4a3f-9ebe-e3fd540b3855 pri=1            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

[COLOR="Red"]# /dev/sda1[/COLOR]
[COLOR="Red"]UUID=7106b2d0-f606-49b9-93cc-6aeb2cf202da[/COLOR] /home/backup ext3 defaults 0 2
[COLOR="Red"]# /dev/sda2[/COLOR]
[COLOR="Red"]UUID=13024ea4-d52a-4e12-b818-6984c23b3c96[/COLOR] /home/music ext3 defaults 0 2
```

---

### Post by Fraoch on 2008-05-14
Perfect!  That worked just fine!

Thanks very much Chris!  One day I'll have to learn about UUIDs.

---

### Post by chrisccoulson on 2008-05-14
No problem! UUID's are just a unique identifier a partition gets when you create the filesystem (Universally Unique Identifier I think). Because UUID's don't change (unless you format the filesystem), they provide a more consistent way of identifying a disk compared to using device nodes (/dev/xxxx). Device nodes are volatile and with removable drives about, you can't always guarantee your disks will get the same device node each time you boot, which means you can have problems mounting filesystems (if the device node for your root filesystem changes, then the system won't boot).

There are ways for manipulating UUID's You've already used 'blkid', which allows you to see what partitions have UUID's and what the device node of that partition is. You can also look in /dev/disk/by-uuid, which contains sym-links to each disks device node (dev/xxxx).

You can change or assign UUID's for ext2/3 partitions using tune2fs (man tune2fs). You can assign random UUID's or a time-based UUID. This is useful if you end up with 2 filesystems that have the same UUID. This normally only ever happens if you clone a whole filesystem.

---

### Post by Fraoch on 2008-05-14
So it looks like what we've done to fstab is to point everything but the md devices to UUIDs and commented out the device node entries.  This will prevent things moving around in future upgrades.  Makes a lot of sense Chris, thanks again.

I suppose it would be possible to identify /dev/md0 and /dev/md1 using their UUIDs too?  It's probably not as necessary provided I don't plan on installing other mdadm sets and since md1 points to / it might be a bit dangerous (get one UUID character wrong and / is unavailable).

Now I'll plug in the USB drive and see what happens. :)

---

### Post by chrisccoulson on 2008-05-14
I'm not familiar with mdraid, but I don't think you need to use UUID's for these because /dev/mdx devices don't depend on the underlying disks having persistent identifiers (I think)

---

