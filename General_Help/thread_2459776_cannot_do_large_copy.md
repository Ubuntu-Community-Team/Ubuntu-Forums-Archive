---
title: "cannot do large copy"
date: 2021-03-25
forum: General Help
---

### Post by jgw on 2021-03-25
I am trying to copy some files to a 64gb memory stick.  When I select the files I want to copy I checked the properties that I am trying to copy and it tells me that there are 4.2gb of files to copy .  When I try and copy the files it gets to around 5gb and tells me there is no more room.  I then goto the memory stick and am told that there is 5? gb left.  I am currently trying to send groups of around 3gb at a time and that seems to be working.  I am using files program to transfer the files.  Perhaps I should be using a different program like krusader or midnight commander.  

Thank you................

---

### Post by HermanAB on 2021-03-25
What file system is on the memory stick? By default a memory stick comes with an ancient DOS file system which is not good for real work. If you want to use it with Linux only, reformat it with ext4 or xfs and if you want to use it with Windows, format it with ntfs.

---

### Post by TheFu on 2021-03-25
FAT32 has a single file size line of 4G, so no file over that size can be copied to any partition using FAT32.
If you format the flash driver to use either exFAT or F2FS, then you shouldn't see the problem anymore.  exFAT might need the exfat-utils package installed and the f2fs-utils, respectively.   F2FS is a native Linux file system, so all the permissions, owner, group are fully supported. It is also very fast according to performance tests.  For Linux backups to flash, the f2fs is an excellent file system choice.  If the data needs to be read by Windows, then exFAT would be a better choice, but it doesn't support owner, group, permissions, ACLs, or xattrs. That makes it a poor choice for a backup, but probably fine for pure data like music or videos or office-productivity files.

BTW, are you 100% certain the flash drive isn't a fake one that says 64G on the outside, but only allowed 4-8G in reality?  The described behavior reads exactly like a fake flash drive would show. For some years, fake flash storage was a huge problem from online sellers.

Besides those ideas, I have 1 more.  Use rsync to copy large amounts of data to other storage.  rsync is smart. If it fails for any reason, re-running the same command will pick up where it left off and continue. Of course, it cannot overcome file system size limitations or fake storage devices, but if the 64G device truly has a file system without the limits/issues above, then rsync is the way.

---

### Post by jgw on 2021-03-25
Thank you for the replies

TheFu
I think you have nailed it.  I reformatted the file to FAT as this is going to a daughter who uses windows and to make sure I did fat.  I will know better next time!

Thanks again!

---

### Post by HermanAB on 2021-03-25
With Windows, NTFS is he best file system to use on a memory stick.  It is a journaled file system and will not become corrupted when the device is unplugged prematurely, as frequently happens with small removable devices. To reformat the device, do so on a Windows system, then Linux can read/write to it.

---

### Post by jgw on 2021-03-26
Yah - I was not sure but knew that fat would work.  thanks for the reply!

---

