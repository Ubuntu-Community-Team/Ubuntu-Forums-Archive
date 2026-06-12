---
title: "ntfs-3g file sharing - permission denied"
date: 2013-08-03
forum: General Help
---

### Post by doogiekd on 2013-08-03
hi friends,
please note the following problem connecting to a windows share.

setup: ubuntu box with a ntfs formatted external hard drive.

the problem: connecting to a shared folder (from a windows or ubuntu machine) on external hd results in "permission denied."

my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda5 :
UUID=fef3e680-94eb-46c0-88e7-d8d728ef6f03	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=A4F23C87F23C602A	/media/administrator/cylon1	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
UUID=26df1336-4912-4ed4-808b-dffec0244fb0	none	swap	sw	0	0

#UUID=90857e85-b177-4c6d-a16f-96925c87f816	none	swap	sw	0	0


my smb.conf file i added:

#======================= Global Settings =======================

[global]

usershare owner only = false

any suggestions in how i can fix the password problem so i can access these windows shared files without the permission error?

---

### Post by GwL3eNC on 2013-08-03
Hallo,

i normaly do nothing special for this. I open my dolphin as sudo, right click the folder i want to share and
select in the properties of the folder a user which can access. He use his username and passwd to access.

If i want to mount a share i take something like that

sudo mount -t smbfs smb://192.168.2.28/projects/myProject /mnt/myProject

192.168.2.28 is the ip adress of my computer with the share on it. /project/myproject the path and the share name.
Hopefully it brings you further

---

