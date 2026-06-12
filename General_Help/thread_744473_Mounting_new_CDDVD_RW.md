---
title: "Mounting new CD/DVD RW"
date: 2008-04-03
forum: General Help
---

### Post by malre1 on 2008-04-03
I have just replaced my CD ROM with a CD/DVD RW machine and although the system does see it their it is not mounted. Could someone please give me or point me to where I can get clear instruction on how to mount. In the partitions settings it sez

Device    /dev/scd0
Mount point    /media/cdrom0
FS type         udf,iso9660
Mount options  user,noauto,exec

I would like it to be auto mounted.

Thanks and regards

---

### Post by Despot Despondency on 2008-04-03
I believe you don't mount the driver itself, rather you mount any cd/dvd you put into the drive. Once you put the disc in go to the terminal and use the command

mount -t type dev dir

where 

type is the type of file system, e.g iso9660 or ntfs, it will usually say the type

dev is the dev/sdc0 part you were talking about

dir is the point you want to access the files from, e.g /mnt/mycd

Once you've done that if you go to /mnt/mycd you should see your files.

Don't know if this is want you wanted, but hope it helped anyway.

to unmount use the command

umount dev

regards

---

### Post by malre1 on 2008-04-03
Thank you for you reply but it keeps telling that /mnt/mycd does not exist.
I really wanted some command that you could tell the system Kubuntu 7.10 to auto mnt when you put a 
CD or DVD in the machine

---

### Post by Despot Despondency on 2008-04-04
/mnt/mycd was just a suggestion, if you haven't made the folder then it won't exist. I think cd's and dvd's are mounted automatically in ubuntu, I was just telling you the mount stuff for general purposes, e.g. external hard drive. Have you looked around in your /media folder when you have a cd/dvd in the drive? I think mine usually goes to /media/cdrom or /media/cdrom0. let me know how it goes.

---

### Post by malre1 on 2008-04-04
Thanks for your help but I am having a very hard job to mount this equipment.
When I go into System Settings>Advanced>Disk & Filesettings it shows up as follows

Burner DVD RW AW-G170 /media/dvd auto /dev/scd0  Disabled 

and even if I go into 'Administrator' for the life of me I just cannot get it 'Enabled'

I have tried command line also but can't seem to fire it up

---

