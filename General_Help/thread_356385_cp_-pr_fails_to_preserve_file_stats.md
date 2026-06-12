---
title: "cp -pr fails to preserve file stats"
date: 2007-02-08
forum: General Help
---

### Post by asalford on 2007-02-08
cp -pr failes to preserve file ownership, last access time and date stamp, and last modified time and date stamp info.

I am trying to create an bash script to cron back up some critical data and must preserve the file charateristics.

i am backing up to a smb share on an nslu2 linksys device.

the nslu2 had been modified to release its full potential.

the error message when running cp -pr is cannot preserve ownership or time stamp.  operation not allowed.  it does copy the file, it just does not preserve the file characteristics.  

is this because it is a smb share?

any work arounds?

would you set up a nfs share off the nslu2?

---

### Post by ^rooker on 2007-02-08
1) it is VERY likely that it's related to being a smb share.

2) You could consider using "rsync" for doing backups...


Sorry for not being more helpful. :(

---

### Post by TyphoonJoe on 2007-02-08
I agree is is related to it being samba.  You could confirm by doing a test backup to a linux native filesystem.

A potential solution is to use the "tar" command to package what you need to backup, that way the file attributes are preserved as part of the archive, not in the fileystem.  Then when you restore the tar file the permissions/time stamps are correct.  

If you are new to tar the basics are:

create archive:

```
tar -cvf yourtarfile.tar file1 file2 file3 dir1 dir2 dir3
```

restore archive:

```
tar -xvf yourtarfile.ar
```

Good luck!

-TyphoonJoe

---

### Post by asalford on 2007-02-08
Thanks for the feedback and you confirmed my suspicions

cp -pr works on the native filesystem and is how I started to believe it was something to do with the smb share even though the device runs busy box.

the linksys nslu2 is a linux running busy box and the drive is ext2  Guess I will have to explore NFS for this mission :)  nothing rules like linux and window stinks everytime.:lolflag:

---

