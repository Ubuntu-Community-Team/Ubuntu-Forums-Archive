---
title: "Looking for Data Recovery Software to recover data from a formatted NTFS laptop."
date: 2008-02-19
forum: General Help
---

### Post by kazuya on 2008-02-19
What do you guys recommend as the best and cheapest option to Recover deleted files from lost, damaged, formatted or reformatted NTFS partition. 

Looking for Data Recovery Software to recover data from a formatted Windows File Systems(NTFS) PC.

Is there a free alternative? If not what are the best options in your opinion? I am based in the U.S.A.

I have heard of SystemRescueCD    and  GetDataBack .. Are these the best and do these let you select what you want to recover? What are the limitations.

One more point, the laptop was formatted from NTFS to reiserfs and then back to FAT32.. Would these still work for it?

---

### Post by bigken on 2008-02-19
[ontrack]("http://www.ontrackdatarecovery.co.uk/data-recovery-software/") data recovery

---

### Post by Rhubarb on 2008-02-19
You could try out an app in the ubuntu repositories called **testdisk**
```
sudo aptitude install testdisk
```

Once installed, you have 2 tools at your disposal to recover files.
One is **testdisk**, which is good for recovering general files.
The other is **photorec**, which is excellent for recovering photos.

These are both command line utilities to be run from the terminal.
I can't help you out with how they're used, either look up the man pages for it, or do a search online.

---

### Post by weigh2tall on 2008-02-25
jA combination of DDRescue and foremost helped me recover an NTFS flash pen that had had the partition deleted during a windows install.  It appears to have worked great!  

Using this post I installed GDDRescue and foremost on my computer and was able to get somewhere. 
Thanks!
[https://help.ubuntu.com/community/DataRecovery#head-bc5f26e6f89d1575ef1ad5cbbac70982a0d86f55](https://help.ubuntu.com/community/DataRecovery#head-bc5f26e6f89d1575ef1ad5cbbac70982a0d86f55)

---

### Post by weigh2tall on 2008-02-25
A combination of DDRescue and foremost helped me recover an NTFS flash pen that had had the partition deleted during a windows install. It appears to have worked great!

Using this post I installed GDDRescue and foremost on my computer and was able to get somewhere.
Thanks!
[https://help.ubuntu.com/community/Da...c70982a0d86f55](https://help.ubuntu.com/community/Da...c70982a0d86f55)

---

