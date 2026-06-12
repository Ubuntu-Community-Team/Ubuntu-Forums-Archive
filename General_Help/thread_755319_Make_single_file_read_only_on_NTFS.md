---
title: "Make single file read only on NTFS"
date: 2008-04-14
forum: General Help
---

### Post by chrisstankevitz on 2008-04-14
Using ubuntu, I wrote a file out to an NTFS drive.  Now I want to make the file read-only so I don't accidentally overwrite it.  chmod doesn't seem to do the job:

```
root@cstankevitz-laptop:/media/lacie# mount | grep lacie
/dev/sda1 on /media/lacie type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)
root@cstankevitz-laptop:/media/lacie# touch test.txt
root@cstankevitz-laptop:/media/lacie# ls -l test.txt
-rwxrwxrwx 1 root root 0 2008-04-14 15:08 test.txt
root@cstankevitz-laptop:/media/lacie# chmod 000 test.txt
root@cstankevitz-laptop:/media/lacie# ls -l test.txt
-rwxrwxrwx 1 root root 0 2008-04-14 15:08 test.txt
root@cstankevitz-laptop:/media/lacie# chmod a-w test.txt
root@cstankevitz-laptop:/media/lacie# ls -l test.txt
-rwxrwxrwx 1 root root 0 2008-04-14 15:08 test.txt

```

Question: How to I make a single file on an NTFS mount read-only?

Thanks,

Chris

---

