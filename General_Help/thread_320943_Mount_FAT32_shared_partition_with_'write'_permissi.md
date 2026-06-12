---
title: "Mount FAT32 shared partition with 'write' permission"
date: 2006-12-18
forum: General Help
---

### Post by coady on 2006-12-18
I have a simple but annoying problem. I want to automatically mount a shared data partition at boot-up in order to read/write data and to share email and web browser information. I have a separate partition formatted to FAT32 (vfat). I have created a mount point (/winshare) and added a line to '/etc/fstab'. For various reasons I would prefer to have an independent mount point rather than mounting it in '/home/user_name' (where I assume I would have read/write access by default). However, while the partition mounts, I can see and access the data, I cannot get write permission.

Here is the relevant information.
$ mount:
```
/dev/sda2 on /winshare type vfat (rw,uid=1000,gid=1000)
```
'/etc/fstab':
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>       		<dump>  <pass>
proc            /proc           proc    	defaults        		0       0
usbfs		     /proc/bus/usb	usbfs		devmode=0666  	  0	0
sysfs           /sys            sysfs   	defaults        		0       0
tmpfs           /dev/shm        tmpfs   	defaults        		0       0
/dev/sda5       /               reiserfs	defaults        		0       1
/dev/sda1       /media/sda1     ntfs		ro,umask=000,nls=utf8		0       0
/dev/sda2       /winshare	vfat		auto,rw,uid=1000,gid=1000 0       0
/dev/sda6       /home		ext3		defaults        		0       0
/dev/sda7       none            swap		sw              		0       0
/dev/hdc        /media/cdrom0   		udf,iso9660 user,noauto		0       
0OC
```

I have tried mounting the partition using <options>:
"rw,auto,users"
and
"defaults"
as well as what you can see above
"auto,rw,uid=user_name,gid=group_name"

I have also tried to run '# chmod' on the mount point, for e.g., '# chmod ug+w /winshare' but while I can change all these options, I cannot change the write permission.

Can anyone advise me on this? Thanks.

coady

---

### Post by bernied on 2006-12-18
try adding the umask option
From man mount:
```
umask=value
    Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current process. The value is given in octal.
```I think this is the (inverse/complement?) of the permissions. So maybe umask=002 would give you rw for user and group. The option rw doesn't seem to be in the list of fat mount options.
To try it out before committing to fstab:
```
sudo umount /dev/sda2
sudo mount -t vfat -o umask=002,uid=1000,gid=1000 /dev/sda2 /winshare
```...I think...

---

### Post by taurus on 2006-12-18
Or

```

/dev/sda2       /winshare	vfat     defaults,umask=000    0       0

```

---

### Post by coady on 2006-12-19
Thanks to everyone who helped out here. I now have read/write access to the shared partition. Best regards to all...:-D 
coady

---

