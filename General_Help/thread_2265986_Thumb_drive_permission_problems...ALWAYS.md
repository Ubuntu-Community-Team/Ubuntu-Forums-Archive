---
title: "Thumb drive permission problems...ALWAYS"
date: 2015-02-19
forum: General Help
---

### Post by sofasurfer on 2015-02-19
I use my thumb drive on my home linux pc and on a work windows pc. I put stuff on it and after a few times using it at home and at work I suddenly don't have permissions to save files to it.
On this most recent journey into locked-out land I reformatted my thumb drive as fat32 using Gparted. The permissions are now set to me=create/delete...group=none...others=none. Then I tried to copy files to it and I am unable because of permissions. I tried to change permissions in the properties tab but they just revert back to original. 

What I want to do is 1) learn why I lose the ability to add files and 2) change permissions so anyone and everyone can add and delete files.

---

### Post by bab1 on 2015-02-19
> **sofasurfer said:**
> I use my thumb drive on my home linux pc and on a work windblows pc. I put stuff on it and after a few times using it at home and at work I suddenly don't have permissions to save files to it.
On this most recent journey into locked-out land I reformatted my thumb drive as fat32 using Gparted. The permissions are now set to me=create/delete...group=none...others=none. Then I tried to copy files to it and I am unable because of permissions. I tried to change permissions in the properties tab but they just revert back to original. 

What I want to do is 1) learn why I lose the ability to add files and 2) change permissions so anyone and everyone can add and delete files.

With FAT file systems the permissions are set at mount time.  When a storage device that is connected by USB is inserted, the udev rules create the mount instructions.  The logged in user is the owner of the files and directories under these conditions normally.  

Copying files is not the same as creating files.  Who is the owner of the files you are trying to copy to the thumb drive?  I believe **cut and paste** will solve your problems of trying to **copy** the files.

---

### Post by nerdtron on 2015-02-19
First formatting the drive as fat32 should solve your permission problem since permissions won't be honored on a fat32 or ntfs file system.

So the problem may lie on mounting the drive? If you are mounting the drive via the GUI, then you should not have any problems. What is the permission of the folder that the drive is mounted?

provide output from the following commands, when the drive is mounted and you cannot write to it.
```
lsblk
cat /proc/mounts
```

---

### Post by sofasurfer on 2015-02-19
Its the 7.5 gig drive

lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 233.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   171G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0  58.8G  0 part /media/daryl/Backup
&#9492;&#9472;sda5   8:5    0     4G  0 part [SWAP]
sdb      8:16   1   7.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.5G  0 part /media/daryl/DCDE-2F62
sr0     11:0    1  1024M  0 rom

---

### Post by sofasurfer on 2015-02-19
I have reformatted to ext4 with no improvement

---

### Post by bab1 on 2015-02-19
> **sofasurfer said:**
> I have reformatted to ext4 with no improvement
What is the mount point and what are the permissions there?

From the terminal what do you get with this command with the drive plugged in```
ls -l /media
```...I assume that the device is mounted somewhere in /media.

---

### Post by sofasurfer on 2015-02-19
> **bab1 said:**
> What is the mount point and what are the permissions there?

From the terminal what do you get with this command with the drive plugged in```
ls -l /media
```...I assume that the device is mounted somewhere in /media.

Mounted in /media/daryl

$ ls -l /media
total 12
drwxrwxrwx+ 3 root root 4096 Feb 19 16:41 daryl
drwxr-x---+ 2 root root 4096 Jun 27  2014 guest-abYeJU
drwxr-x---+ 2 root root 4096 Feb 19 16:40 terry

$ ls -l /media/daryl
total 4
drwxrwxrwx 3 daryl daryl 4096 Feb 19 04:49 2f992fc7-f4ff-4d11-87ae-9fab5235fdc7

$ ls -l /media/daryl/2f992fc7-f4ff-4d11-87ae-9fab5235fdc7total 16
drwxrwxrwx 2 root root 16384 Feb 19 04:49 lost+found

---

### Post by sofasurfer on 2015-02-19
Never mind. I think I fixed it. I was not editing the permissions in media, only the thumb drive. Seems to be working now...for now. But I still do not understand why, when I edited the thumb drive permissions they would not stay as I set them.

---

### Post by bab1 on 2015-02-19
> **sofasurfer said:**
> Never mind. I think I fixed it. I was not editing the permissions in media, only the thumb drive. Seems to be working now...for now. But I still do not understand why, when I edited the thumb drive permissions they would not stay as I set them.

EXT file systems do not work like FAT or NTFS file systems.  You can fully set the owner and permissions with EXT.  But the file system can't be read by native Windows means.  NTFS and FAT file systems canonly have the owner and permissions set at mount time.  NTFS can't be read by Apple OSX.  FAT can be read by Linux and OSX along with Windows.  This is why FAT is used on USB connected devices.  It's portable.

The choice (as always) is yours.  If this is just a Linux drive I would leave it as EXT4  If you need Windows and Linux only then NTFS (or FAT).  If you need compatibility with Windows, Linux and OSX then FAT is the only file system to use.

The limitation with FAT is the 4 GB file size.  EXT and NTFS do not have this limit. 

Hope this helps.

---

### Post by sofasurfer on 2015-02-19
If I go with FAT, should I wait and format it on the windows pc at work? You said that on linux, permissions are set to the system that formats it. So if I am going to use it here and there I should format it on winblose.

I currently have it formatted with EXT4. When I use it on windows it may lose its permissions again, correct?

---

### Post by bab1 on 2015-02-19
> **sofasurfer said:**
> If I go with FAT, should I wait and format it on the windows pc at work? You said that on linux, permissions are set to the system that formats it. So if I am going to use it here and there I should format it on windows.

I currently have it formatted with EXT4. When I use it on winblose it may lose its permissions again, correct?
I didn't say that at all.  The ownership and permissions are set when the file system on the USB stick is **mounted **into the file system of the host computer.  

With a FAT file system the ownership and permissions are not integrated in the formatting.  It doesn't matter what OS formats a FAT file system.  You don't loose what is not there.  When I insert a brand new USB storage device that has never been a part of my system it shows my user name as the owner and the permissions are set by the UDEV rules for mounting that device.

---

