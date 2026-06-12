---
title: "Hard Disk questions/Anti Virus"
date: 2007-02-10
forum: General Help
---

### Post by Entity` on 2007-02-10
Has anyone ever found an easy way to mount NTFS drives WITH READ & WRITE access???
Im trying to migrate entirely to linux without the using windows as a crutch.

==OR==

Is there a way to convert NTFS drives to RieserFS or simalar without moving any data from the drive in question and still be able to retain the data after conversion??

I know Partition Magic can do this, but the version I have DEMANDS a stupid Floppy drive; of which I do not have the luxury of nor do I have the luxury of transferring data from the drive(s) in question.

As an afterthought can someone please give me the Command lines to install AVG free for LINUX on here?

Thanks in advance for all your help.

---

### Post by etank on 2007-02-10
As far as read write support for NTFS, I have a USB drive that I use. It is formatted as NTFS so I installed ntfs-3g and then added this line to my /etc/fstab
```
/dev/sda1     /media/usbdrive     ntfs-3g     users,silent,umask=0002,locale=en_US.utf8,no_def_opts,allow_other    0    0
```Now the drive auto mounts and I can read and write to it with no problems.

---

