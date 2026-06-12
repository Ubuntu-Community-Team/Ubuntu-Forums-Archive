---
title: "mp3/data dual question"
date: 2005-10-16
forum: General Help
---

### Post by Vanish00 on 2005-10-16
First off, I've tried looking for information on how to get access files from my Windows XP.  One of the files being my music files.  The information I come accross is mount/umount and somehow remember what partition has those files....i think.  My problem is how do I see all of my partition again ( i have 2 Hdd ).  Is this the process I need to take in order to grab my files from windows?

---

### Post by Vanish00 on 2005-10-16
bump

---

### Post by objorkum on 2005-10-16
Run this command:

sudo fdisk -l

Paste output here.

---

### Post by randomc0de on 2005-10-16
0. "mkdir /media/Windows"
1. "su"
enter your password
2. "fdisk -l"
one of the drives listed will use the FAT32/NTFS filesystem, remember the name
3. "mount -t ntfs -o umask=0 /dev/<hard drive> <path to mount folder>"
where hard drive is the guy from step 2, and path to mount folder is the windows folder you created

The "mount folder" now has all your Windows files.

4. ???
5. Profit!

Oh yeah, I don't know what to do for the mount command to specify FAT32, but you'll probably use NTFS, and "mount --help" or "man mount" should do the trick.

---

### Post by invisage01 on 2005-10-17
check the ubuntu starter guide!! [http://www.ubuntuguide.org/#automountntfs]("http://www.ubuntuguide.org/#automountntfs")

there is a section there on windows - NTFS and FAT32 .. you can only read NTFS.. but you can read/write fat32 ... 

there are instructions there for just doing it on a one off basis or for editing the fstab for boot up mounting :D

cheers

---

