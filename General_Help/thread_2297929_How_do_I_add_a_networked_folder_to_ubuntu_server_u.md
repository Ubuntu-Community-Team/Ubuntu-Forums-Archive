---
title: "How do I add a networked folder to ubuntu server using terminal?"
date: 2015-10-07
forum: General Help
---

### Post by david_brown on 2015-10-07
Hi,

I have a Ubuntu server I use for Plex media server. I'd like to mount a folder on another box (Raspberry pi) to the Ubuntu. I've created a mount point /media/pi where I would like it to be added and the address I'm trying to add is //192.168.1.115/mnt/usb. I am trying to mount it manually at this point and haven't made any changes to /etc/fstab

I've tried mounting it manually with sudo mount //192.168.1.115/mnt/usb /media/pi cifs username=username,password=password 

It doesn't mount and I get the following:-

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount 

Not entirely a newbie, but at the bottom end of the learning curve!

---

### Post by SeijiSensei on 2015-10-07
Don't use SMB for Unix-to-Unix file sharing.  Use NFS instead.  

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

---

### Post by david_brown on 2015-10-07
I was going to add that the file I want to mount from the pi is ntfs system.

---

