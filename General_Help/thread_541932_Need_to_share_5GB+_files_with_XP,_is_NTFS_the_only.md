---
title: "Need to share 5GB+ files with XP, is NTFS the only option?"
date: 2007-09-03
forum: General Help
---

### Post by drywater on 2007-09-03
I Have read that NTFS is very unstable in general, especially in linux and that ext3 is the preferred system.  However, I must be able to share the mounted drives with a networked windows system (using samba).  FAT32 would be fine except that I am using the linux box as a storage server for video and constantly needing to store files larger than FAT32's 4GB file limit. usually 10GBs or so, which is why I have opted to use NTFS.

My question is, is there another file system- more stable than NTFS- that both linux AND windows can recognize AND not limit the file size?  Am I going to find this to be more trouble than it is worth to use linux?

I did have everything running in Windows just fine, but decided it was time to try linux again.  Not to degrade linux, but is what I am trying to do acceptable for linux or will I have faster/more reliable performance using Windows on both boxes?

Thanks!

-Stephen

(ps, I did get samba running but ran into some problems auto-mounting which spurred this question)

---

### Post by Happy_Man on 2007-09-03
Well, no. There are ext3 drivers for Windows, that work really well, and ext3 is better than NTFS by a long shot. Plus, Linux will automagically defragment the volume for you every now and then. Those drivers can be found at  [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by drywater on 2007-09-03
Thanks for the info.  I did a search on the file size limit of ext3 and cannot find anything definite except that is supports "LFS" (Large File Size).  Is there a limit?  I am going to try it right now.

Thanks again!

---

### Post by drywater on 2007-09-03
Well I installed the mentioned program but it does not see networked drives, therefore the networked Ext3 drive is unusable in XP. I will search for an answer but do you have other ideas of a workaround or a different program to enable Ext3 access on a networked drive in Winxp?

---

### Post by Happy_Man on 2007-09-03
> **drywater said:**
> Thanks for the info.  I did a search on the file size limit of ext3 and cannot find anything definite except that is supports "LFS" (Large File Size).  Is there a limit?  I am going to try it right now.

Thanks again!
I'm not sure what the block size is for Ubuntu, but Wikipedia says that with a block size of 4 KiB, it will go up to a max file size of 2 TiB, and a max filesystem size of 16 TiB. So don't worry.

---

### Post by vanadium on 2007-09-03
If you are using samba to share the files over the network, then just stick to ext3.

---

