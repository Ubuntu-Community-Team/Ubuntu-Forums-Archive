---
title: "NTFS on 4th partition file deletion. Dual Boot MCEs"
date: 2008-04-06
forum: General Help
---

### Post by himpantsou on 2008-04-06
Hi all,
I have a system setup with
dual boot for Ubuntu and Windows XP
I have 4 partitions
a) Windows using NTFS file format i installed Windows Media Centre
b) On Ubuntu 7.10 Gutsy using ex3 file format i installed MythTV
c) Ubuntu Swap file
d) I created a 4th partition again in NTFS format to store all my MP3 and TV recordings

I followed [http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g_p3](http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g_p3)
and now the 4th partition in loaded automatically on Ubuntu bootup and can read all media.
In fact i can create folders and write files from Ubuntu.

My problem is that when i use MythTV to record a TV program it records them fine on the 4th NTFS partition and i can replay them but when i reboot after the recording, the TV file Myth saved, vanishes.


One thing i did notice. As soon as Myth writes a file in a directory,  "nfslockfile.lock" file is created in that directory....

Can anyone help?

---

