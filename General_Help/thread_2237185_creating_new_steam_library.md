---
title: "creating new steam library"
date: 2014-07-31
forum: General Help
---

### Post by reid2 on 2014-07-31
I'm trying to create a new steam library on a different hard drive to the one Ubuntu is installed on but when i create the new folder i get an error message that says "New Steam library folder must be on a file system mounted with execute permissions". How do I fix it?

---

### Post by tgalati4 on 2014-07-31
Open a terminal:

```
sudo chmod +x /media/username/nameofdirectorywhereyourstreamsarelocated
```

---

### Post by mcduck on 2014-07-31
Is the drive in question formatted using a native Linux filesystem (such as Ext4), or are you trying to use a FAT or NTFS partition?

If it's a Linux FS, then you really shouldn't be having any issues with it, as setting execute permissions can be done for each file when required. But you can always check the /etc/fstab i case there's some mount option specifically preventing files to be set as executable.

If it's a Widndows filesystem, however, things get a bit more difficult as the filesystem itself isn't capable of understanding Linux permissions. Even then it's possible to force all FAT/NTFS filesystems to mount with execute permissions, but that's a bit more complicated (and also could be seen as a security issue).

---

### Post by reid2 on 2014-07-31
Its formatted to FAT 32, so should i move my data off it and reformat it to Ext4?

---

### Post by mcduck on 2014-08-01
Yes, you'd definitely get less problems and better performance using a native Linux filesystem. And that would solve the permission problems as well.

The only reason to use a Windows filesystem is if you need to share the partition with a Windows install on the same machine, and even then I'd recommend using NTFS instead of FAT. And really considering if all the files need to be shared or if having two partitions, one for Linux and a smaller one for sharing, would work.

---

### Post by reid2 on 2014-08-01
ok thank you very much. Still very new to ubuntu

---

### Post by adgsfuzwe on 2015-01-25
I'm another user with the same problem. The solution is easy: You have  to mount a partition with "exec". I didn't wanted to change my old  partitions or the fstab-file, so I created a new partition with ext4.  BTW the old partition I used for Steam games was NTFS. I use Ubuntu  14.10 64-bit and the newest Steam. After I created a partition with the  GUI of gnome-disk-utility (a really great program [http://wiki.ubuntuusers.de/Laufwerksverwaltung](http://wiki.ubuntuusers.de/Laufwerksverwaltung)),  I clicked on the partition, then on these 2 circles, then on mounting  options edit, then in the first line I switched the button to OFF. There  is a line which contains "nosuid,nodev,nofail,noauto,x-gvfs-show", just  add ",exec" and click ok. Then use Steam.

---

