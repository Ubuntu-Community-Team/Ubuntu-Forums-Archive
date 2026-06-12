---
title: "external hard drive won't mount after hardy upgrade"
date: 2008-05-03
forum: General Help
---

### Post by kei-clone on 2008-05-03
my fantom external hard drive won't mount/connect properly anymore ever since i upgraded to hardy. if i try to access it from dolphin, it freezes half the programs that I'm running, and if I do an ls in /media, i get this message:
> ls: cannot access keicompclone: Input/output error
cdrom  cdrom0  keicompclone  keicompclone-1  sda1  sda2

where keicompclone is the name of my external. can anyone help me with this?

---

### Post by ibuclaw on 2008-05-03
type in "**ls -l**" in the /media directory.

What is the filesystem type of the partition? (ie: ext3, ntfs, fat)

Also, can you copy and paste the line in your fstab line which shows the mount info of it (if it exists). Type in "**gedit /etc/fstab**".

Regards
Iain

---

### Post by kei-clone on 2008-05-03
ls -l:
> ls: cannot access keicompclone: Input/output error
total 20
lrwxrwxrwx 1 root root        6 2008-03-18 20:06 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2008-03-18 20:06 cdrom0
d????????? ? ?    ?           ?                ? keicompclone
drwxrwx--- 1 root plugdev 12288 2008-04-24 00:10 sda1
drwxrwx--- 6 root plugdev  4096 1969-12-31 19:00 sda2


it is an ntfs filesystem, but I do have ntfs-3g installed. again, this problem occured only after upgrade to hardy. in addition, occasionally I am able to access the drive, but it seems to be at random times, or at least i can't reproduce when i can and when i can't access the drive

it's not in my fstab, and I don't think it should be because it doesn't mount on startup am i correct?

---

### Post by kei-clone on 2008-05-04
bumpity bump?

---

### Post by FrooziE on 2008-05-04
My external drive mounts and I can browse it, but cannot copy,change, move, edit, rename or do anything to any of the files. It simply says "Error removing file: Input/output error". All permissions are set, I'm logged in as root anyway and still nothing.

---

### Post by kei-clone on 2008-05-06
I still can't get this to work, and seems i'm not the only guy having problems. can i get some help here plz?

---

### Post by kei-clone on 2008-05-09
help? :(

---

### Post by kshtjsnghl on 2008-05-09
You might try installing the ntfs configuration tool. that might help you

try typing this in terminal - 

sudo apt-get install ntfs-config

after it gets installed you can access it through applications > system > ntfs configuration tool.

Besides check if it is showing the drive in gparted and if there is no useful data on it try deleting it.

if gparted is not installed on your system - 

sudo apt-get install gparted

Try it might help you.

---

### Post by kei-clone on 2008-05-10
> **kshtjsnghl said:**
> You might try installing the ntfs configuration tool. that might help you

try typing this in terminal - 

sudo apt-get install ntfs-config

after it gets installed you can access it through applications > system > ntfs configuration tool.

Besides check if it is showing the drive in gparted and if there is no useful data on it try deleting it.

if gparted is not installed on your system - 

sudo apt-get install gparted

Try it might help you.

i couldn't get ntfs-config to work, perhaps something to do with the fact that i'm running kde here. i'm not about to delete my drive with gparted either >_>

i dunno if this helps, but this is what happens when i compare these two commands:

> kei-clone@kei-comp:~$ ls /dev | grep sd
ptysd
sda
sda1
sda2
sda3
sda4
sda5
sda6
ttysd
kei-clone@kei-comp:~$ mount | grep sd
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
/dev/sda6 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type vfat (rw,utf8,umask=007,gid=46)


actually right now, I'm having an even bigger problem as it seems i'm unable to mount ANY external storage devices, whether they be an external HDD or a usb drive or an ipod. i could really use some advice here :(

---

### Post by kshtjsnghl on 2008-05-10
I think its actually out of my league coz  i m a noob too. 
Try to post the same thread on the absolute beginner forums also.
i think there might be more help to you over there in those forums..

---

