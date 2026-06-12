---
title: "Write access to Flashdrive"
date: 2008-06-12
forum: General Help
---

### Post by gavinjb on 2008-06-12
Hi,

I am having a problem with my 4gb Flash drive where I can write data to the root but not to any of the sub folders as I only have read access to them, the drive is fat32 so I am not sure why I don't have access, can anyone help?


Thanks,



Gavin,

---

### Post by simonasambler on 2008-06-12
It is not a Hard Drive so it can happen that it mount only -ro so you have to mount manually.
First umount you pendrive, find out which is you usbkey to do this type 
```
sudo fdisk -l
```
when you find out which it is umount them /usually, when you have  one HDD it is sdb/ so type to terminal 
```
sudo umount /dev/sdb
``` or change sdb to sign of your usbkey 
than when you have all done you have to mount again but in rw mode to do this first create a file in your /media folder /for example usbkey/ and then mount your usbkey by command 
```
sudo mount /dev/sdb /media/usbkey -t vfat -o rw
``` 
/again whe your usb key is no a sdb change it /
all done, now it shoul work in rw mode .

---

### Post by gavinjb on 2008-06-13
Hi,

I think you misunderstood, it isn't that the drive is ro, it is that all subfolders are, e.g.

if drive mounts as /media/usbflash then

/media/usbflash is writerable but /media/usbflash/Documents is readonly

Gavin,

---

### Post by timcredible on 2008-06-13
the only time i've seen a flash drive not writable is when there's an error on the drive.  windows never checks for errors, it just writes to it no matter what, even if the data is getting corrupt while writing.  do a dosfsck on the drive from a terminal session to check.  if there are errors, do a dosfsck -a

---

### Post by gavinjb on 2008-06-13
Thanks, but didn't make any difference, in the end I found that doing a sudo chmod +rw to the folders fixed it, but I would not have expected to do that to a fat32 device that had the folders created in windows.

I am also having a similar problem when attaching any ext2/3 device, but this time they are mounting as readonly for my normal user, is there anyway without adding an entry to fstab for every drive to give my normal users to write to these drives.


Thanks,

---

### Post by simonasambler on 2008-06-13
Oh , a didnt read it correctly :) . So it doesnt work, only with chmod ? So this is about permission to subfolder. I try to man chmod and it looks like chmod -R should fix it .

---

