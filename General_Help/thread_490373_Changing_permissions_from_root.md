---
title: "Changing permissions from root"
date: 2007-07-02
forum: General Help
---

### Post by Dak1n on 2007-07-02
Hi,

I have a hard disk that I have all my media stored on but I cannot add any files to it as the permissions for the whole disk are set to root. I have tried in terminal:

*sudo chmod a+rwx /media/Files*

**(Files is the name of the hard disk)**

Then it says:

chmod: changing permissions of '/media/Files' : Read - only file system

but I still can only read from the hard disk.

I'm quite new to Linux so any help would be greatly appreciated.

Thanks.

---

### Post by r0ck80y on 2007-07-02
Is the hard disk ntfs ? If yes, then you need to install ntfs-3g to enable write permissions.

---

### Post by Qu4k3R on 2007-07-02
See also chown command

> man chown


after installing ntfs drivers

---

### Post by Dak1n on 2007-07-02
ok, thanks, i will install

---

### Post by Dak1n on 2007-07-02
hi, i'm still having problems, i installed the software, then tried

sudo chown -hR administrator /media/Files

and after it has done all the processes it says

chown: changing ownership of '/media/Files': Read-only file system

and i still cannot edit the files

---

### Post by Dak1n on 2007-07-02
any help on this would be greatly appreciated

---

### Post by TrueJk7 on 2007-07-02
I'm getting the feeling this is a Flash memory device. Or at least an external file system hence the "/media/". If you are working it and it's a FAT system you may want to check out the dosfsck command. Or at least what is listed in this testing wiki

[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

---

### Post by Dak1n on 2007-07-02
hi,

it isnt a FAT system, its in NTFS, and it isnt Flash memory, its a normal IDE hard disk.

---

### Post by r0ck80y on 2007-07-02
If you are on feisty, go to System tools --> NTFS Configuration Tool. This will enable the ntfs-3g modules to give write permissions. Or in terminal type "sudo ntfs-config"

---

### Post by Dak1n on 2007-07-02
if i try it in terminal is just says

make sure you have the 'universe' component enable
bash: ntfs-config: command not found

---

### Post by r0ck80y on 2007-07-02
Please post your /etc/fstab file. Also type this in terminal and post its output:```

aptitude search ntfs-3g
```

---

