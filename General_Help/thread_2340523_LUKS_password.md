---
title: "LUKS password"
date: 2016-10-19
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-10-19
I have a flash drive encrypted with LUKS.  Last year I forgot my password, but formatted it somehow.  I'm trying to do it again, but forgot how.  Can anyone help me out?  :confused:

---

### Post by TheFu on 2016-10-19
[https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems)

I use dm-crypt via **cryptsetup** to handle LUKS for non-OS drives. For the OS, I've never been able to manually get it working, so stuck with the automatic partitioning during installation (which isn't what I want).  

I suppose there are many ways to encrypt things. I've always done it at the partition level, then used LVM with PEs, VGs, and LVs to slice up the encrypted volumes.  I know that Caja (a file manager) knows how to ask and access portable storage encrypted in this way. I haven't seen any of the other file managers recognize it, but haven't looked in a few years either.

BTW, you can have upto 8 different passphrases for each LUKS volume. I have a 65+ character passphrase, plus a 10-character AND Yubikey passphrase (32? characters?) for quicker access most of the time.  If you care about security, it would be smart to use a password manager for stuff like this. It won't help with physical logins or initial whole disk decryption, but you can store all other passphrases you need and have them each be different for every need without having to track them in 10 different places or remember them at all.  KeePassX is a F/LOSS password manager.

Anyway, hope this helps.

Overview:
* select/create the partition to be encrypted
* use cryptsetup to encrypt the partition
* Either
** use mkfs -t ext4 pointing at the encrypted partition to add a file system
or
** use pvcreate, vgcreate and lvcreate to make the LVs (basically extremely flexible partitions)
** use mkfs -t ext4 pointing at the LV(s) to add a file system
* use mount or edit the fstab to mount the file system(s) as desired.  These won't happen at boot. Boot file system mounting needs the initrd and crypttab updated in some manner.

Anyway, hope this isn't too confusing and actually helpful.

---

