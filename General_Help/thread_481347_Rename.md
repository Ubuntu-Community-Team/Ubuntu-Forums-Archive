---
title: "Rename"
date: 2007-06-22
forum: General Help
---

### Post by fred0843 on 2007-06-22
I have a number of Partitions setup up on my Hard Drive (ext3) for Data storage.They show on the Desktop as hda 6 Etc.Is there a way to rename them On the desktop an in File Manager?

---

### Post by luscinius on 2007-06-22
if I understand correctly their names come from the mount points specified in /etc/fstab
For instance, I had a line like

UUID=462F-CD2A  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1

for a fat32 partition. It should be possible to change "/media/hdb1" to say "/media/*new_name*" (say /media/D)and restart the kernel. Also make a backup of /etc/fstab before editing it. Probably you will also have to create the new mountpoint (/media/D in this example) manually,
```
sudo mkdir /media/D
```

---

### Post by YoG%*@ on 2007-06-22
i'm not sure, but this may be of help to you: 
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")
worked fine on my external hd. 

hth
mux

---

