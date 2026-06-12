---
title: "Defrag FAT32 from Linux?"
date: 2005-04-13
forum: General Help
---

### Post by chapterthree on 2005-04-13
Hey All,

I have two disks on my system, I have my Ubuntu (ext3) disk, and a FAT32 disk, which is used as a data disk to store data that can be accessed by both Windows and Linux.  Basically I have this machine running as a file server.

Is there any way to defragment the FAT32 drive from Linux?

Thanks

---

### Post by nad on 2005-04-13
The only linux utilities I know of to manipulate dos, fat and vfat filesystems are mkfs.dos | fat | vfat, dosfsck and several partitioning programs.

I understand that you may wish to keep the vfat partition for compatibility reasons. If this is not required, then simply copy everything to a new ext2/3, reiserfs, xfs, etc filesystem. Also, the easiest and quickest way to defrag any M$ filesystem is to copy everything to a newly formatted clean partition of your filesystem choice. This can certainly be done from linux. And remember that's ' cp -dpR /somefilesystem/* /mnt/some_other_filesystem/. ', not the dd command.

Dan M

---

### Post by shakin on 2005-04-13
[QUOTE=chapterthree]Basically I have this machine running as a file server.[/QUOTE]

If it's a network file server then the filesystem doesn't need to be FAT. Samba uses smbfs to share so Windows never knows what the underlying filesystem is.

If you're dual booting and use the FAT partition to allow files to be copied from one OS to the other, then you should probably just boot into Windows to do the defrag. From there you can even convert the  drive to NTFS. Hoary should happily mount it in r/w mode.

---

### Post by chapterthree on 2005-04-13
Great, thanks for the suggestion, I didn't even realize the Samba thing.  Yes, it is a fileserver, so it is a networked box, and the disk is being shared with Samba, so I'll convert it over to ext3 :)

Thanks again!

---

