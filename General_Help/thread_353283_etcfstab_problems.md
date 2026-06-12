---
title: "/etc/fstab problems"
date: 2007-02-04
forum: General Help
---

### Post by sputnik2012 on 2007-02-04
Hi all.

I've made an ext2 filesystem on /dev/hda4, and wish to mount it as /media/hda4.  I can mount it normally using **mount /dev/hda4 /media/hda4**.

I've added the following line to /etc/fstab:
[B]UUID=62be5403-0116-41b5-ba35-56ccef164623 /media/hda4   ext2    defaults,umask=007,gid=46        0       0
[/B]

When I run mount -a I get the following output
> mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/62be5403-0116-41b5-ba35-56ccef164623,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


What am I doing wrong?

Thanks,
     Rob.

---

### Post by taurus on 2007-02-04
Make to make the entry in /etc/fstab to look like this then.

```

/dev/hda4   /media/hda4   ext2   defaults,umask=007,gid=46   0   0
```

---

### Post by empthollow on 2007-02-04
it should work fine line this
```
/dev/hda4 /media/hda4 ext2 defaults,umask=007,gid=46 0 0
```
if you get the same error try 
```
fsck /dev/hda4
```

---

### Post by sputnik2012 on 2007-02-04
As I said, it mounts fine using the **mount** command.  Just won't load from /etc/fstab.  I've replaced the uuid label with /dev/hda4, still no joy.

It only works when it's formatted using vfat, with 
**#UUID=45BC-9D42 /media/hda4     vfat    defaults,umask=007,gid=46       0      0**.

 Are there any other files associated with the drive, like System.map? 

Thanks, 
         Rob.

---

### Post by taurus on 2007-02-04
Okay, you need to decide if /dev/hda4 is ext2 or vfat because you have both in there!  Also, try not to use UUID; instead, use /dev/hda4 in /etc/fstab.

---

### Post by sputnik2012 on 2007-02-04
The vfat line is commented out, and I've tried using /dev/hda4 in place of the UUID to no avail.  Maybe I'm not using default codpepages, do you know where they are set?

I changed the drive back to a vfat one to see what would happen, and it automounts fine like that, but for some reason it won't automount when I'm using ext2. Will try ext3 to see if it makes a difference.

---

### Post by sputnik2012 on 2007-02-04
Works using ext3 with default options. Will leave it like that.

---

### Post by taurus on 2007-02-04
So you are saying that /etc/fstab would mount /dev/hda4 as vfat but won't mount it as ext2!  Then, it is a vfat filesystem.

Do you want to format it to ext2?

---

### Post by sputnik2012 on 2007-02-04
Aye, that's with running mkfss.<xxx> a few times, it's a bare drive, but yes it works in /etc/fstab when it's fornatted with vfat and ext3, but not as ext2. The problem probably lies in the options part, or autoloading the kernel module, but now it's loading I'll leave it as is.

Thanks,
       Rob.

---

