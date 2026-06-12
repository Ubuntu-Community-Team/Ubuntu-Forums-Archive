---
title: "Permissions of SMB mounted share"
date: 2012-11-30
forum: General Help
---

### Post by dannyboy79 on 2012-11-30
I have a Western Digital My Book World Edition, which is a NAS enclosure. It has 1 share on it and is set to allow everyone read/write/execute per the web gui settings. When I mount it using cifs options like uid=1000,gid=1000 I look within nautilus at /mnt/circle/ and it just shows all the folders and files within that folder are permissions - and unknown. What does that mean? Is nautilus not able to read permissions, user and group of SMB shares?

I am assking because I am currently using rsync to sync a dieing 1TB hard drive to this WD My Book World Edition and rsync is giving me errors like not being able to set time, invalid arguement:22 and also errors on all folders saying no such file or directory exists despite it in fact being there. So rsync appears to be working (backing up evertyhing on the 1TB drive to the public share on the WD My Book WE) but why does it give these errors. Any thoughts?

---

### Post by 2F4U on 2012-11-30
From your post I understand that you get the data copied but have problems with certain attributes such as time and permissions. Is this correct? One idea that comes to my mind would be that the filesystem on the WD maybe doesn't support these permissions. Do you know what the filesystem is on the WD?

---

### Post by SeijiSensei on 2012-11-30
Most commercial external drives are formatted with NTFS or FAT32, neither of which support *nix permissions.  You have a couple of choices if managing permissions and datestamps is important to you:

1)  Reformat the drive as ext4.

2)  Create two partitions on the drive and format one with NTFS for Windows users and one with ext4.  Export the latter with Samba.

3)  Create a tarball of the files you want to back up, then copy the tarball to the external drive like this:

```

cd /
sudo tar cjvpf homes.tar.bz2 home
mv homes.tar.bz2 /path/to/external/drive

```

---

### Post by dannyboy79 on 2012-11-30
no i don't know what filesystem it is but according to this [http://en.wikipedia.org/wiki/Western_Digital_My_Book#Internals](http://en.wikipedia.org/wiki/Western_Digital_My_Book#Internals)
they are xfs or ext3

---

