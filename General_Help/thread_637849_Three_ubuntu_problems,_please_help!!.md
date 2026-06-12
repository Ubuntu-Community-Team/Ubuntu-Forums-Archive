---
title: "Three ubuntu problems, please help!!"
date: 2007-12-11
forum: General Help
---

### Post by tomlj on 2007-12-11
I would like to get ubuntu working as I like however I have the following issues:

1. About 50% of the time ubuntu freezes on boot, as the progress bar is about at 1/8th complete. If I reset the PC it mostly works. 

2. I can't work out how to auto mount my smb net shared drive. I've pasted fstab below. If I mount -a it appears, but I'd prefer it to do this on boot.

3. I accidentally removed the top panel with  the 'apps' 'places' and 'system' etc tabs and icons.
I replaced it and put everything back as it was, although now I don't get notifications of updates. How can I restore this behavior?

Fstab
>  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=177eabca-46a4-4c5e-b9af-25745d12a3de /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=688ed0af-aeac-4413-af44-ff3427698480 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



#Added by diskmounter utility
/dev/hdc1 /media/hdc1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda1 /media/hda1 vfat rw,user,fmask=0111,dmask=0000 0 0

//thomson/BT_7G /media/nfs smb auto,iocharset=utf8,uid=tom,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

blkid
> /dev/hda1: TYPE="ntfs" 
/dev/hdc1: TYPE="ntfs" 
/dev/hdc2: UUID="177eabca-46a4-4c5e-b9af-25745d12a3de" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdc5: UUID="688ed0af-aeac-4413-af44-ff3427698480" TYPE="swap" 

Thanks in advance!
Tom

---

### Post by matthewcraig on 2007-12-11
>>  3. I accidentally removed the top panel with the 'apps' 'places' and 'system' etc tabs and icons.  I replaced it and put everything back as it was, although now I don't get notifications of updates. How can I restore this behavior?

Isn't that the Notification Area applet?

---

### Post by mali2297 on 2007-12-11
Problems 1 and 2 are probably related, I think others can give you better help on fstab though.

As for Problem #3, look for *notification area* among the choices to add to the panel.

---

### Post by tomlj on 2007-12-11
Thanks for the help with #3, two to go!

---

### Post by matthewcraig on 2007-12-11
Sounds like you do not have all the required processes running when you try to shoehorn the SMB mount.  Put the mount -a command in your user login scripts instead, and you'll might stop causing the boot process to lock up, too.

---

