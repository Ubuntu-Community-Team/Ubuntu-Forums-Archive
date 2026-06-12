---
title: "Can't change permissions on my third partition"
date: 2007-05-30
forum: General Help
---

### Post by solecki on 2007-05-30
Hi
My problem is that I've mounted my system partition (were Windows is installed, C:\) to /media/SysPart and I can read and execute all files from any user account in there (dr-xr-xr-x 1 root root 8192 2007-05-29 15:21 SysPart). Ok so everything is allright there.

__The problem is that my other partition were i store all my media files and such is not accessable from any other account than root.__

When I try to change mode for it I get this message:

sudo chmod g+rx /media/SecPart/
chmod: changing permissions of `/media/SecPart/': Read-only file system

What can I do so I can access my third partition (/media/SecPart)?

Any help is apreciated

---

### Post by empthollow on 2007-05-30
i have had similar problems, my first question is how are you mounting this partition. please post command line or /etc/fstab entry.

---

### Post by solecki on 2007-05-30
> **empthollow said:**
> i have had similar problems, my first question is how are you mounting this partition. please post command line or /etc/fstab entry.

I mounted the sda5 (SecPart) partition with these commands:

sudo mkdir /media/SecPart
sudo mount /dev/sda5 /media/SecPart

---

### Post by empthollow on 2007-05-30
try this after unmounting the drive
```
sudo mount -O users /dev/sda5 /media/SecPart 
```
the users flag allows users to access the drive
...also
i noticed the permissions on the drive do not include other to read or write to the drive and that root is the owner. in order to view the files you would need to be in a root group or be root. to make it readable by all users type
```
sudo chmod -R a=rx /media/SysPart
```
to make writeable by all use
```
sudo chmod -R a=rwx /media/SysPart
```
if you want to change the owner of the files type
```
sudo chown [username] /media/SysPart
```
this is not necessary if the permissions are set to let others read the drive.

---

### Post by strabes on 2007-05-30
You should do ```
sudo chown username:username /media/SysPart
```

This will change the group of the folder to your user's group as well.

---

### Post by solecki on 2007-05-30
hmm I tryed this command: sudo mount -O users /dev/sda5 /media/SecPart, but it's still the same as it was before, I can't change mode for users for it; Read-only file system :/ really weird ..

---

### Post by empthollow on 2007-05-31
what file system is it?

---

### Post by solecki on 2007-05-31
It's NTFS
Btw I've got both my NTFS partitions (SecPart + SysPart) read and execute accesseble, but not writable. I got them rw accessable by using the ntfs-config system tool wich i downloaded..but lol, I don't know how to get the partitions writable.

---

### Post by empthollow on 2007-05-31
ntfs-config did the trick for me but when i first installed it didn't work right away, i went into the config tool a couple times and then it let me write to it.  seems to me it might have taken a minute to refresh or something.  my partition is loaded via fstab however and i have a few more options on it.  maybe that has something to do with it.  i'll check when i get home, i'm at work and don't have access to my system.

---

