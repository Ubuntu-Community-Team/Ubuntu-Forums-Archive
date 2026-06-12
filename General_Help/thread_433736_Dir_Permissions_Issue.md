---
title: "Dir Permissions Issue"
date: 2007-05-05
forum: General Help
---

### Post by Koloth on 2007-05-05
Hi All,

I have finally made the jump to Kubuntu after being with Windows for so long and as I wasn't keen in eventually going the way of Vista.
It looks like Linux has greatly improved for the desktop since I last used it so many eons ago for general use.

Anyway I need some help with permission issues.

I have 2 FAT 32 drives (Rig1 & Rig2) with all my files mounted as follows (etc/fstab):

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=bc944716-91c8-44e1-b121-6d408a9ca8fa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=31269291-c9de-4665-ae7f-7b1a630be1b3 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda2
/dev/hda2 /mnt/rig1 vfat umask=0000 0 0
# /dev/hdc1
/dev/hdc1 /mnt/rig2 vfat umask=0000 0 0


Now I can access these folders and files but one particular dir doesn't give me permissions to change/modify/delete it.

The properties of the folder (shaun), under the permissions tab are set as "Can View Content".

I have tried the following commands from reading:
sudo chown -R shaun /mnt/rig2/shaun     
I get this response:
chown: changing ownership of `/mnt/rig2/shaun': Operation not permitted

I've also tried:
sudo chmod 755 -R /mnt/rig2/shaun
but this makes no difference either.

I would appreciate any help in resolving this greatly.  I don't want to go back to Windows unless I have to.  If things go well I was planning to uninstall my windows partition in a couple of weeks :-).

---

### Post by aysiu on 2007-05-05
You can't *chown* or *chmod* Windows partitions.

Try this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

