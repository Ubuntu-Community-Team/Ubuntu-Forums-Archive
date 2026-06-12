---
title: "Create Drive letter for external USB device"
date: 2015-12-07
forum: General Help
---

### Post by chris405 on 2015-12-07
Hello, in Windows I have a Plex server setup and have it linked to my Movies on Drive F: which is my external USB drive and I was able to move the installation over to Ubuntu 15.10 and have Plex server install but my external USB drive doesn't show up as F: in Ubuntu, just says My Passport ( /media/user/.....) so was wondering if there is a way to Create/Map and virtual drive letter or whatever to my external USB drive to make it also an F: drive in Ubuntu? Thx

---

### Post by yancek on 2015-12-07
> but my external USB drive doesn't show up as F

It won't because Linux doesn't use the partition naming conventions using upper case letters, a carry over from operating systems developed forty years ago.  If you want to name it 'F' you can do it.  Is your external drive always connected?  You create a mount point in the /mnt or /media directory using:  sudo mkdir /media/F or sudo mkdir /mnt/F.  You would then put an entry in the /etc/fstab file with the options you want.  You can find lots of examples online or post more specifics on what you want including the filesystem on the partition.

---

### Post by pqwoerituytrueiwoq on 2015-12-07
use [Gparted](apt:gparted) and name the partition of the flash drive 'F'
then you will get a icon on your desktop labeled 'F'

what ever the partition name is is what it will be when it is auto-mounted
[FONT=courier new]/media/$USER/$Partition_name[/FONT]

---

### Post by HermanAB on 2015-12-07
...and to be pedantic, the DOS/Windows device name is actually "F:" so set the memory schtick label to "F:" and you will get a thingummy on the desktop called that.

---

### Post by chris405 on 2015-12-08
Ok, thx for the answers. I'll give it a go.

---

