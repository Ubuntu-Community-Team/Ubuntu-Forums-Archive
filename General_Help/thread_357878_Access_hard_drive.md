---
title: "Access hard drive"
date: 2007-02-10
forum: General Help
---

### Post by bossa on 2007-02-10
How do you get access to files /folders on yourhard drive when using Ubuntu as a live CD ?. I am using NTFS Hard drive is that a problem?

---

### Post by taurus on 2007-02-10
Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t /dev/hda1 /media/windows -o nls=utf8,umask=0222
df -h
```
Assuming /dev/hda1 is where your Windows is.

---

### Post by bossa on 2007-02-10
Hi Taurus
I copied and pasted what you put in your post and I am assuming it mounted the Hard drive which  is /dev/hda1 going by what it says in device manager. Sorry but I dont know where to find it (/dev/hda1). I have been looking in computer>filesystem but iI cant see /dev/hda1. Where should I be looking?
Thanks Steve


I found /dev/hda1 but it says cannot open /dev/hda1 no application is known for this kinf of file

---

### Post by EdThaSlayer on 2007-02-10
> **bossa said:**
> Hi Taurus
I copied and pasted what you put in your post and I am assuming it mounted the Hard drive which  is /dev/hda1 going by what it says in device manager. Sorry but I dont know where to find it (/dev/hda1). I have been looking in computer>filesystem but iI cant see /dev/hda1. Where should I be looking?
Thanks Steve


I found /dev/hda1 but it says cannot open /dev/hda1 no application is known for this kinf of file

You can find out whether it is /dev/hda1 or /dev/hda2 or something else just by starting the Gparted program which you should be able to find in:
System->Administration->Gnome Partition Editor.

---

### Post by bossa on 2007-02-10
> **EdThaSlayer said:**
> You can find out whether it is /dev/hda1 or /dev/hda2 or something else just by starting the Gparted program which you should be able to find in:
System->Administration->Gnome Partition Editor.

Definately /dev/hda1

---

### Post by bossa on 2007-02-10
I want to install Ubuntu as a dual boot with XP ,if I install Ubuntu will I be able to see and use whats on my windows hard drive or am I going to use FAT32? Doesn't seem to be able to do it it right now. I used Ubuntu ,Mepis ,Knoppix etc etc with my previous machine which was a FAT32 Hard drive and did not have this problem.

---

### Post by taurus on 2007-02-10
> **bossa said:**
> Hi Taurus
I copied and pasted what you put in your post and I am assuming it mounted the Hard drive which  is /dev/hda1 going by what it says in device manager. Sorry but I dont know where to find it (/dev/hda1). I have been looking in computer>filesystem but iI cant see /dev/hda1. Where should I be looking?
Thanks Steve


I found /dev/hda1 but it says cannot open /dev/hda1 no application is known for this kinf of file

It's mounted to /media/windows.

```
ls -la /media/windows
```

---

### Post by bossa on 2007-02-12
after copying and pasting I get this :

mkdir: cannot create directory `/media/windows': File exists
ubuntu@ubuntu:~$ sudo mount -t /dev/hda1 /media/windows -o nls=utf8,umask=0222
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
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ df -h


What should I do ?

---

### Post by bossa on 2007-02-13
Well I'm going to dual boot with XP pro and see what happens .Strange that I cant access the files on the Windows Hard drive .Just used Mepis as a Live CD and had no problem looking at and using files .

---

### Post by bossa on 2007-02-16
OK well I'm dual booting with Windows NTFS and I go to /media/windows. and thereis nothing there . How do I get to see the Files on my Windows partition?

---

### Post by charl.ie on 2007-02-16
```
sudo mount /dev/hda1 /media/windows
```
This will mount it, so you can access the files. If you want to see the files when you turn the computer on, then you will have to edit /etc/fstab.
```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab &
```
Add:
```
/dev/hda1       /media/windows      ntfs    defaults,nls=utf8,rw 0       1
```

---

### Post by bossa on 2007-02-16
Thanks charl.ie
But after doing that I get permision denied?

---

### Post by charl.ie on 2007-02-16
Sorry, prehaps I was not clear. After
```
sudo gedit /etc/fstab &
```

I meant add "/dev/hda1       /media/windows      ntfs    defaults,nls=utf8,rw 0       1" into the window that opens.

Instead of that, run:
```
sudo bash
echo "/dev/hda1       /media/windows      ntfs    defaults,nls=utf8,rw 0       1" >> /etc/fstab
exit
```
p.s What background do you have, from what I can see it looks really good.

---

