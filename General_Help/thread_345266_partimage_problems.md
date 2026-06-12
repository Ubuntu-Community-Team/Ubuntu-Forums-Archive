---
title: "partimage problems"
date: 2007-01-24
forum: General Help
---

### Post by the.phantom on 2007-01-24
ok i have the self booting cd and trying to use partimage but having major problems (probably cockpit trouble)

i installed a second ide hard drive and it is hdb1 and only has the one partition on it 
it works find in 6.10 ubuntu

when i boot off of the cd after saying 41 for us keyboard
it comes up to the prompt


by all the directions that is when i should enter in 

mkdir /backup


it tells me that is not a valid command

no matter with or without that space, 

ok i tried the next step 
mount/dev/hdb1
and 
mount/dev/hdb1/backup and doesn't like those either


so i went on and read the many ways to use partimage and even went to their site and printed instructions

on their site he is using a command
/mnt/backup/linux-redhatXXXX.gz


so i figured i would try several things there

such as 
hdb1
hdb1/backup ( and even have a folder there)

and says it can't backup

so i tried the sites way of
/mnt/hdb1/backup
no luck
and
/mnt/htb1

that worked but said the disk was full after a short time but it was looking at the other drive as said i had 36 free space


hdb1 is a 40 gig and the new hdb2 is a 80 gig

this is what fstab shows on ubuntu in case this helps some?
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9e7bde7a-574c-47dd-bf8b-ba3f72dbdd2a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=10d42f9f-4a43-48c9-8192-5f5465550924 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb/storage ext3 defaults 0 0
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
been trying for hours and as i said get nowhere on the first command prompt when the bootable disk is ready
but i can enter in partimage there and it will load the program?

any help would really be appreciated

as spent 2 days getting the second drive to work  and getting a bit wired on this as the only reason i put in the second drive was for backup

thanks
mitch


any idea what i can be doing wrong?

---

### Post by the.phantom on 2007-01-24
ok i finally figured it out
it took 3 "how to use partimage sites" to get one set of directions that would work
some had things in a wrong order
and it is hard to use exact spaces with working on a print out !

but the main thing was to mount the drive on the live cd BEFORE you do anything !

not after checking for partitions as i had to mount to see the partitions ;-D

and to set the size bigger than the backup space !

---

