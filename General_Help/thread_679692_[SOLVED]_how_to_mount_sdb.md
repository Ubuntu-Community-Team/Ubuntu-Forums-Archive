---
title: "[SOLVED] how to mount sdb?"
date: 2008-01-27
forum: General Help
---

### Post by LoneWolfJack on 2008-01-27
ok, I have two raid volumes in my machine: a raid 0 (sda) for linux and a raid 1 for backup purposes (sdb).

so far, I managed to install everything on sdb1 and partition sdb2. sdb2 shows on my desktop as "disk" and with a drive icon, but unless I Iog in as root, I can't write to this disk.

what I'd like to achieve is to automatically run a backup script that zips and copies all critical data to sdb2 once every hour. as long as only root can write to sdb2, I would have to enter the root password every time the script runs, which I don't want to do.

so the questions are:
... how to I get write permissions for that drive (chmod doesn't work)?
... and if there's no way to directly do that, can I somehow mount the drive to a folder I can write to? 

thanks for your help.

---

### Post by BuffaloX on 2008-01-27
In terminal type

> sudo nautilus

Navigate to your /media
create a folder you could rename it to backup or data or whatever
(This folder is used as a mountpoint for your drive.)
Right click the folder, and enable permissions to read and write.

Check the right name of your partition using gparted. (partition editor)
Now mount the drive like this:
> sudo mount /dev/sdb1 /media/data

---

### Post by BuffaloX on 2008-01-27
If you want to be able to mount without entering your password/use sudo.
Make a small bash script "backup"
In terminal write
>  chmod u+s backup  

---

### Post by LoneWolfJack on 2008-01-27
thanks, got it.

interestingly, I had tried mounting the drive before but it always failed with "no block device" or "operation not permitted"...

---

### Post by BuffaloX on 2008-01-27
Weird, but nice you got it working now. :)

---

