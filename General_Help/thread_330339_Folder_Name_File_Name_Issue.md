---
title: "Folder Name/ File Name Issue"
date: 2007-01-03
forum: General Help
---

### Post by wizzkid on 2007-01-03
Hi,

I have a tar format file and i extract it on FAT32 partition on my Ubuntu system, however, I encounter error says:

The extraction operation failed.

Upon checking the extracted folder, some of folder with capital latters became small latters. I tried to create a folder in capital letters, but it became small letters as well.  

Here's my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=19c0c3fc-c5ff-4403-be5b-cb4bafa18303 / reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=9f119fec-6f02-428f-a158-d9cf08b9a06b /boot ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=93ea947a-1da9-4c3e-8236-529f1282aad3 /home reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6 none swap sw 0 0
# /dev/hda7 -- converted during upgrade to edgy
UUID=447B-0C43 /media/data vfat iocharset=utf8,umask=000,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
-- end

Is there a way to correct this issue? 

your response to this matter is highly appreciated.


TY

---

### Post by jblebrun on 2007-01-03
FAT filesystems are case-insensitive. So, you will often see odd changes in case when working with a FAT FS in linux. As for why the tar extraction failed, I am not sure. Are all your files there? If there were files that had the same name but different case, that would create issues on a FAT filesystem. I'd suggest trying to extract the tar file on a normal Linux filesystem, and then see what happens if you try to copy everything over to the FAT drive. You may get more details about what is making it unhappy.

---

### Post by wizzkid on 2007-01-03
Hi Thanks for your response.

When I extract the tar file on FAT FS, it has error but all files are extracted. On Linux/Reiserfs works fine, no error.

Is there a workaround on using Captial and Small letter as a foldername/ filename on FAT FS (mixed)?  (etc. MyProject). 

Reponse to this matter is highly appreciated!


TY

---

### Post by jblebrun on 2007-01-05
If you can, re-create the partition as VFAT. If it must be FAT16 or FAT32, you need to change the charset for that filesystem, and I have no idea how to do that.

---

