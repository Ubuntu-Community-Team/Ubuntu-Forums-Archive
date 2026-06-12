---
title: "windows partition permissions"
date: 2007-04-20
forum: General Help
---

### Post by Mateo on 2007-04-20
If I go to Places, my windows partition is not listed.  However if I go to "Computer"  it is listed, though it shares the same icon as my removable drives, not the icon of the non-removable drives.  If I double-click on it from "Computer" it is accessible (though in the past i've had to type in a password first.

is this some type of permission problem or a mounting problem or what?  here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=ecdaa542-3247-4c3e-a636-1f3364a23575 / ext2 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=3234-38EB /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=8C98CE4098CE2912 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda4 -- converted during upgrade to edgy
UUID=821b8b71-36f4-46d4-a959-04c375f82430 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

sda2 is the partition i'm talking about.  Note that it says ntfs but that is wrong because I converted it to fat32.  do I write in "fat32" instead of ntfs or do I write "vfat" or what. thanks.

---

### Post by Mateo on 2007-04-21
bump

---

### Post by Mateo on 2007-04-21
bump

---

### Post by Mateo on 2007-04-22
bump

---

### Post by Mateo on 2007-04-22
bump

---

### Post by jpeddicord on 2007-04-22
I believe you use "vfat" for the partition, however if that does not work you may try "fat32".

Jacob

---

### Post by Mateo on 2007-04-24
changed it, but i still have to type in a password before I can access the drive.

---

### Post by Mateo on 2007-04-25
bump, is there something in fstab that makes me have to type in the root password to access the partition in nautilus?

---

### Post by Mateo on 2007-04-26
bump

---

### Post by Mateo on 2007-04-28
bump

---

### Post by Erlander on 2007-04-28
Are your user names the same for both Windows and Ubuntu?

It can help if they are.

Rob

---

### Post by Mateo on 2007-04-28
No... I don't have a username for the windows partition.  Also, it's the same set up (username wise) as when both were working.  This problem only ocurred after I converted the windows partition to fat32.

---

### Post by Mateo on 2007-05-02
So, I tried using the "chown" command hoping that would change something.  It didn't.  I'm still guessing this is some kind of mount problem, but I have no idea what the problem is.

---

### Post by Mateo on 2007-05-03
bump.

---

### Post by Mateo on 2007-05-04
bump.

---

### Post by Mateo on 2007-05-06
bump.

---

### Post by strabes on 2007-05-06
Get rid of all this business: > **Mateo said:**
> nls=utf8,umask=007,gid=46 0 1

If your partition is fat32 you should use "vfat" instead of ntfs.

My mounted windows drive line in fstab looks like this:

> /dev/sda1       /media/windows  ntfs-3g defaults        0       0

It's that simple. No read/wrlite/permissions problems or anything.

---

### Post by Mateo on 2007-05-07
Did it, no change.  Still have to click on the drive in nautilus and type a password before it can be used.  This is my fstab now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=ecdaa542-3247-4c3e-a636-1f3364a23575 / ext2 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=3234-38EB /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=8C98CE4098CE2912 /media/sda2 vfat defaults 0 0
# /dev/sda4 -- converted during upgrade to edgy
UUID=821b8b71-36f4-46d4-a959-04c375f82430 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

so if its not fstab, what else could be causing this problem.

---

### Post by Mateo on 2007-05-08
bump.

---

### Post by TransitMan on 2007-05-08
This is what a portion of my /etc/fstab/ looks like for my Windows partition:

"/dev/sda1 /media/sda1 ntfs noauto,uid=1000,gid=1000,auto,rw,owner 0 0"

Looks like you're using a Windows OS that formatted the drive to ntfs. If so, you need to change that back in your /etc/fstab/
You also state that the user names are different between Ubuntu and Windows. Should not really need to be a problem.

Go to "Synaptic Package Manager" and install the NTFS package to let you auto mount the drive with read/write permissions. 
Should you continue to have problems, then you will need to go to the Windows partition and in the Control Panel -> Users put in your Ubuntu username and password.
This way, if and when you want to access the drive you can.

On my system, I can access my XP partition with no problems, but on my server I have to login with name and password.

---

### Post by Mateo on 2007-05-08
It's not NTFS.  It was ntfs, but I converted it to fat32.

---

### Post by Mateo on 2007-05-08
well I think I finally figured out what the problem is.  how to fix it is another story.  when I typed 'mount -a' (just learned this command today) it said:

mount: special device /dev/disk/by-uuid/8C98CE4098CE2912 does not exist

and sure enough, this is about the line in question.  So how do I found out the correct uuid?

---

### Post by Mateo on 2007-05-08
ok, figured it out.  the command blkid gives you the IDs.  I've changed them and going for a reboot to see if it finally works right this time.

---

### Post by strabes on 2007-05-08
You still have the "utf8,umask=007,gid=46 0 1" business in there...

---

### Post by Mateo on 2007-05-08
that was for a different partition.  that's my windows recovery partition.  It never stopped working correctly so I'm not changing it.  I commented it out because I don't need/want it to mount anyways.

---

