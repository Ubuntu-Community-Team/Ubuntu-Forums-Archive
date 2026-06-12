---
title: "[SOLVED] partition access"
date: 2008-06-27
forum: General Help
---

### Post by upchucky on 2008-06-27
Hello there,

I have a ext3 25 gig partition i created to store stuff.

it is /media/sda4

I have a root user
and a simple user, (no pun intended)

my fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-041B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6C74A95574A922B6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1174E0F45EF02D59 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=89ef2fb0-0e3f-46eb-b6af-faffd3dcaf63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /media/sda4 (25gig disk)
/dev/sda4       /media/sda4     ext3       umask=000        0       0

from what i read on the forums this is supposed to auto mount the drive and allow group permissions.
when i mount the drive it asks for root password to mount, then it mounts fine.

when i check permissions it says root is owner, and i can read only, but cant write to drive.

when i chown the drive it says invalid user whether i am root, group or simple user.

sudo chown /media/sda4 user:group

I also tried to make this drive a home drive using the instructions posted here, but it chokes cause it can't write to the drive

my original intent was to create a larger home partition to copy my existing home directory to as it is pretty much full

so now i have my  original 7.10 ubuntu install ext3 at 13gig
and I created a 25gig partition that i cant write to.

first i started with the idea to merge the two partitions, but that failed so i tried to set it up as a storage partition and that worked, but wine cant see it to write to it

so then i tried to do the new home partition with the intent of moving my existing home directory to it when done.

no matter what i try i cant get permission to write to this partition.

---

### Post by drs305 on 2008-06-27
I think you are making this more complicated than it needs to be. Just change your fstab to :
```
# /media/sda4 (25gig disk)
/dev/sda4 /media/sda4 ext3 defaults 0 2
```

Then:
```
sudo chown -R username:usergroup /media/sda4
```

Finally:
```
sudo umount -a
sudo mount -a
```

---

### Post by upchucky on 2008-06-27
Thanks for the quick reply,

the code you posted does not work, it made the drive completely invisible, 

the chown code still says invalid user, I swear to god I'm not an invalid, hehe.


gonna keep tryin, i dont understand how i can edit files as root but cant write to this drive when root. even though it says root is the owner.

---

### Post by drs305 on 2008-06-27
Would you post your fstab:
```
sudo fdisk -l
```

This is an ext3 partition on your primary drive, and you have a mount point named /media/sda4 , correct?

**Added:**
Try running this on the mount point:
```
sudo chmod -R 755 /media/sda4
```

---

