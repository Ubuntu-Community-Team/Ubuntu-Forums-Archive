---
title: "write privileges"
date: 2007-05-23
forum: General Help
---

### Post by rdav@usa.com on 2007-05-23
How can I give myself write privileges?

---

### Post by onbongos on 2007-05-23
chmod u+w /where/ever

---

### Post by taurus on 2007-05-23
You need the write privilege to what directories/files.  Use sudo (or gksudo for GUI) if you need it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bobplano on 2007-05-23
for what? if its a system file then you need to use (gk)sudo, and for partitions you need to mount it with those permissons by editing your /etc/fstab

---

### Post by rdav@usa.com on 2007-05-23
I have a USB drive named "SG400".   If I am in the terminal window, exactly what do I have to type in order to give myself write privileges?

---

### Post by taurus on 2007-05-23
Is it ntfs or fat32 and where do you mount it?

```
sudo fdisk -l
df -h
```

---

### Post by rdav@usa.com on 2007-05-23
I think it is mounted because I can access the files on it, but I don't have write privileges so I can create new files or update what is there...

---

### Post by taurus on 2007-05-23
Can you post the output of those two commands?  Maybe you need to unmount it and remount it again with the write permissions for your USB drive.

Otherwise, you can just drag stuff to it with (if it's fat32 filesystem)

```
gksudo nautilus
```

p.s.  Which release are you running anyway?

---

### Post by rdav@usa.com on 2007-05-23
This is the kind of thing that makes it so difficult for windows users to move to unix.  Everyone who uses unix knows how to do this, but a new user doesn't have a clue.

When you install ubuntu, you do not have write privileges.  What I need to do is give myself write privileges so I can create and modify files on an external usb drive that I can currently read, but not write to.

---

### Post by taurus on 2007-05-23
And what is why I keep asking what filesystem is that USB drive?  You can read and write to fat32 no problem but you need to install ntfs-3g first before you can write to ntfs filesytem.  The ntfs driver that comes with your Ubuntu only allows you to read from it but not write.

---

### Post by rdav@usa.com on 2007-05-23
The file system is ntfs, but the ubuntu that I installed must already have it because I am able to read spreadsheets and word documents with no trouble.  My problem is that I don't have write privileges.

---

### Post by taurus on 2007-05-23
Okay, let's me explain it again.  Ubuntu comes with ntfs driver for your ntfs filesystem but it is a read-only driver.  Therefore, you can read whatever you want on ntfs filesystem BUT you cannot edit or remove files from it.  To do that, you need to install ntfs-3g so you can write to ntfs filesystem.

Which release are you running anyway?

---

### Post by rdav@usa.com on 2007-05-23
ok.  That would explain what is happening, although the messages I get when I try to writel  suggest that the problem is simply that I don't have write privileges.

How do I find the version?

---

### Post by taurus on 2007-05-23
Just post the output of this command here and we will see how to install ntfs-3g driver on your machine so you can write to that USB drive.

```
cat /etc/apt/sources.list
```

---

### Post by rdav@usa.com on 2007-05-23
The version appears to be 7.04 released in April 2007...

---

### Post by taurus on 2007-05-23
Can you post the output of this command from a terminal then since you are running Feisty?

```
sudo fdisk -l
```

---

### Post by rdav@usa.com on 2007-05-23
It says 7.04 Feisty Fawn  Release 1386 (20070415)

---

### Post by rdav@usa.com on 2007-05-23
when I enter "sudo fdisk -1", it asks for my password, then gives me an error message "fdisk: invalid option -- 1"

---

### Post by taurus on 2007-05-23
It's a lower letter l as in larry, not number 1.

```
sudo fdisk -l
```

---

### Post by rdav@usa.com on 2007-05-23
It gives a bunch of technical details about heads and cylinders, blocks, etc.
then it lists three drives (virtual?):  /dev/sda1, /dev/sda2, and /dev/sda3

then it list one more drive:   /dev/sdb1

---

### Post by rdav@usa.com on 2007-05-23
Did you give up?

---

