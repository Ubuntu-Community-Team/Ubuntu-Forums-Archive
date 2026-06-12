---
title: "How to make a mounted HDD not require a root password to access"
date: 2020-06-04
forum: General Help
---

### Post by jgv804 on 2020-06-04
Hi i recently manage to successfully mount a 1T HDD(i added the automatic mount on boot on the fstab aswell) to have extra space to save personal files and games so my SSD can have more space, and without trouble i can pass the files, but since the HDD always requires the administrator password to access, it has made it difficult to install and manage software, is there a way to disable the password for this drive?

---

### Post by SeijiSensei on 2020-06-04
deleted

---

### Post by SeijiSensei on 2020-06-04
deleted

---

### Post by SeijiSensei on 2020-06-04
Let's assume you're mounting the drive as /disk.  Then if you run the command

```
sudo chown -R username:usergroup /disk
```

this will make all files and directories owned by you. Usually your "usergroup" will be identical to your "username."

[Meant to edit the original post, but somehow ended up with it duplicated, probably because I hit reply rather than edit.]

---

### Post by TheFu on 2020-06-04
SeijiSensei's post addresses native Linux file systems.
If the storage is using NTFS or any of the "FAT" types of file systems, **chown** has no impact because those file systems don't support ownership in the Unix way. If the file system isn't known, you can check it after it get mounted using 
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
```
That command doesn't show fake, pseudo-storage, just the real stuff we care about. If you are lazy, **df -hT** works fine too, just with more junk to manually filter.

---

### Post by Impavidus on 2020-06-04
For things like software, games, add-ons that you install system-wide, i.e. for all users, it's appropriate to need root permissions and therefore sudo and your password to install them. You can however set permissions such that some users can put files there without password. Assuming it's a Linux filesystem, use the permissions the way they were designed. Some people set up the staff group and create directories owned by the staff group with the set group ID bit set, so that the somewhat privileged users who are considered staff can change things there without password, but other users can't change things.

---

### Post by jgv804 on 2020-06-04
thanks the chown command worked perfectly :D

---

### Post by VMC on 2020-06-04
> **jgv804 said:**
> Hi i recently manage to successfully mount a 1T HDD(i added the automatic mount on boot on the fstab aswell) to have extra space to save personal files and games so my SSD can have more space, and without trouble i can pass the files, but since the HDD always requires the administrator password to access, it has made it difficult to install and manage software, is there a way to disable the password for this drive?
  
Your saying its the drive and not the files inside the drive that needs pw?
How is this drive attached;usb, sata, etc.

Any drive that I attach doesn't require a pw. I don't have any  external drive mounted via fstab.

edit:ok, it was the files and not the drive itself.

---

