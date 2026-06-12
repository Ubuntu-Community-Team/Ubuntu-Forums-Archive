---
title: "File system for Ubuntu partition"
date: 2015-03-09
forum: General Help
---

### Post by jet-san on 2015-03-09
Hi there,

Recently I installed a new Ubuntu on my PC, so now I have 2 system partition for Win7 and Ubuntu and 2 secondary partitions, also for these systems. Obviously both Win7 partitions are NTFS and I can access them from both operating systems. The Ubuntu system partition is EXT4, so I thought I should use same file system for the secondary partition. However I cannot do any operations on this partition once I formatted it from Ubuntu using GParted. Should I use different file system for the second Ubuntu's partition to be able to save anything on it or am I just doing something wrong?
[[img]http://s12.postimg.org/bhe7vh0zt/Partycje.jpg[/img]](http://postimg.org/image/bhe7vh0zt/)

Thanks,
Damian

---

### Post by mastablasta on 2015-03-09
you need to make it accessible by your user. go to properties in the partition. 
you also need to mount it. it should mount when you open it from nautilus. when you formatted it you probably setup a mount point. usually it's on /media/yourpartitionname

can you explain a bit better what you can't do and what you want to do on the partition?

---

### Post by oldfred on 2015-03-09
You probably want to permanently mount with fstab and then give yourself permission to use it.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

      
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

This will manually mount for one boot and give you owership & permissions.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Good examples of templates to use for permanent mounting with fstab of both NTFS & Linux formatted partitions:

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by jet-san on 2015-03-09
To be honest automatic mount of the partition would be nice, but it is not obligatory. I had this partition mounted and working before the Ubuntu re-installation. Then I formatted my Ubuntu partition and I installed a new version on it, but I have not touched the second partition. When I opened it (mounted) for the first time after format I could see main folder (computer name) and some folders inside. I was able to access them, but I did not check whether I can modify anything. I the main folder with all subfolders and I have noticed I cannot create a new folder on this partition. I thought I might need to format it, so I did it from Ubuntu using GParted. The partition is empty, in ext4 file system and I cannot create or copy anything there... I can mount it, open it, check properties, but I am unable to create a folder/document there or copy anything onto the partition.

Damian

---

### Post by yancek on 2015-03-09
Do you mean you are unable to write or create any files/directories on that partition even as root, using sudo or gksu?  If the partition is ext4 and mounted, you should certainly be able to do that.  Re-formatting a partition isn't going to make any difference as far as a user being able to write to a partition.  Have you tried the chown and chmod commands suggested by oldfred?

---

