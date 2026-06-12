---
title: "mounted NTFS partition, non-root user denied access"
date: 2005-04-23
forum: General Help
---

### Post by usererror on 2005-04-23
is there a way for me to mount my windows xp ntfs partition to my user home directory and have normal user be allowed to read it?

currently after i mount /dev/hda1 to normal user ~/windows    the normal user cannot access it.  only root to view the files.

how can i change this?  thanks. :)

would mounting the partition on bootup make any difference?

---

### Post by jburey on 2005-04-23
don't forget to put the umask option

example:

mount -t ntfs -o ro,noauto,umask=022 /dev/hda1 /media/cdrive

I would add it to the fstab if you are going to use this often

---

### Post by usererror on 2005-04-23
[QUOTE=jburey]don't forget to put the umask option

example:

mount -t ntfs -o ro,noauto,umask=022 /dev/hda1 /media/cdrive

I would add it to the fstab if you are going to use this often[/QUOTE]


i just added that line to fstab:


# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/hda1       /media/windows  ntfs  ro,user,umask=022 0       0

that works brilliantly.

question though, what does "umask=022" do??

---

### Post by tread on 2005-04-23
umask 022 - Assigns permissions so that only you have read/write access for files, and read/write/search for directories you own. 

All others have read access only to your files, and read/search access to your directories.

---

### Post by usererror on 2005-05-03
ah i gotcha.  thanks for the explanation!

---

