---
title: "Wanting to switch, but I have a question."
date: 2007-01-14
forum: General Help
---

### Post by Strag0 on 2007-01-14
Hello,

I want to switch over to Ubuntu from my current Windows install. However, I've got a question before I switch over. My wife and I have several hard drives in this computer that we use for storage. When I switch over I'm curious if I'll be forever stuck not able to access the files. I know that Linux has questionable NTFS write ability. I want to switch, but I don't want to be left without these files or access to the Hard drives. 

Thanks!

---

### Post by aysiu on 2007-01-14
If those drives are FAT32 or Ext3, you can access them from both Ubuntu and Windows (the latter with the help of [http://www.fs-driver.org](http://www.fs-driver.org))

Read more details here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by finer recliner on 2007-01-14
Linux can read NTFS formatted drives just fine. writting to NTFS is still very beta, but is constantly being worked on, and someday it should be possible. In the mean time, I have constanly read my windows files (on NTFS) and edit them in ubuntu, and then save them to a flash drive formatted in FAT32. Then when I go back to windows, I can write over the old file with the new one.

FAT32 formatted drives can be read and written too by linux and windows just fine. because of this, it is common for dual booters to use it as an "exchange location" for their files between OS's. hope that helps.

---

### Post by nix4me on 2007-01-14
fat32 cannot tolerate files over 2gig.  So if you have large files, it won't work.

If you are switching entirely to linux, then move the files off and make the drives ext3 and then move the files back until all the drives are done.  If this computer acts as a file server, you can use samba to share the drives to other windows/linux computers on the network.

nix4me

---

### Post by cowlip on 2007-01-14
ntfs-3g (read/write ntfs) is very reliable.  you will be able to write to it on ubuntu, it's not ntfsmount or captive ntfs...

---

### Post by Theimon on 2007-01-14
> **nix4me said:**
> fat32 cannot tolerate files over 2gig.  So if you have large files, it won't work.


I thought the limit was 4GB? 

ntfs-3g is a very good alternative. I used it when I had a dualboot here. All read/write actions went flawlessly, and I used it intensly. At this point however I have no dualboot any more, so all my drives are ext3.

---

### Post by rabid9797 on 2007-01-14
> **cowlip said:**
> ntfs-3g (read/write ntfs) is very reliable.  you will be able to write to it on ubuntu, it's not ntfsmount or captive ntfs...

to elaborate:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

this will allow you full writing access to your ntfs drives, just follow the directions and everything should work fine

also, if you plan on keeping your windows partition, you should consider installing this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

it will allow you full read and write access to your linux partition

---

### Post by tagra123 on 2007-01-14
> **rabid9797 said:**
> to elaborate:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

this will allow you full writing access to your ntfs drives, just follow the directions and everything should work fine

also, if you plan on keeping your windows partition, you should consider installing this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

it will allow you full read and write access to your linux partition

Ditto this post. I have a similar setup and have experienced 0 (zero) problems.

---

### Post by aysiu on 2007-01-14
> **Theimon said:**
> I thought the limit was 4GB? 

ntfs-3g is a very good alternative. I used it when I had a dualboot here. All read/write actions went flawlessly, and I used it intensly. At this point however I have no dualboot any more, so all my drives are ext3.
You are correct. The file size limit is 4 GB, not 2 GB.

---

