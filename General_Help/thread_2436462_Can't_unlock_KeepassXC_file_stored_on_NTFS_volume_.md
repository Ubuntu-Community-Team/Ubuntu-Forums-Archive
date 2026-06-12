---
title: "Can't unlock KeepassXC file stored on NTFS volume mounted in Ubuntu"
date: 2020-02-06
forum: General Help
---

### Post by linuxguiri on 2020-02-06
In Ubuntu 19.10, I can't unlock a password-protected KeepassXC file stored on a mounted NTFS volume, but if I copy it to an ext4 volume I can open it. I can read and write other file types to the NTFS volume (e.g., odt). 
The NTFS partition is mounted in fstab as: ```
ntfs auto,user,rw 0 0
```
What permissions/options need to be changed in order to unlock the password-protected KeepassXC file on NTFS from within Ubuntu?

[B]EDIT
SOLUTION[/B]
 1. Open Ubuntu Software app and find KeePassXC
 2. Click on Permissions
 3. Toggle "Read/write files on removable storage devices" to on

---

### Post by TheFu on 2020-02-06
[https://github.com/keepassxreboot/keepassxc/issues/803](https://github.com/keepassxreboot/keepassxc/issues/803) may or may not be related. It seems to be a similar issue for DBs on Samba going through gio/gvfs. They describe it as an upstream issue in the Qt File module.

If you manually mount the partition, directly, does that help?
```
sudo mount -t ntfs /dev/somethng /mnt
```

I don't have any NTFS here to test.  I use rsync to copy the DB to 6 different locations every night, so it massively backed up and available as needed.  In my mind, there is only 1 system where changes to the DB are allowed.

Reading more there, 
> disabling the option *Use file transactions for writing databases*
Doing that scares me.  A DB that doesn't support transactions is asking for corruption problems.

---

### Post by linuxguiri on 2020-02-07
Thanks for finding that issues page, TheFu! Well, at least it's not just me. 
As a workaround, I ended up using a syncing service to sync the file to the ext4 volume when in Ubuntu and to the NTFS volume when in Windows.
Thanks again!

---

### Post by linuxguiri on 2020-02-09
**SOLUTION**
 1. Open Ubuntu Software app and find KeePassXC
 2. Click on Permissions
 3. Toggle "Read/write files on removable storage devices" to on

---

