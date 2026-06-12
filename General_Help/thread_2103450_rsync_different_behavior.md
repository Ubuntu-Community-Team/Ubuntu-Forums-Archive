---
title: "rsync different behavior"
date: 2013-01-10
forum: General Help
---

### Post by g.a. on 2013-01-10
hello,

I have two scripts to backup my data using rsync.

One script copy on a networked pc while the other on a mounted external drive. The two rsync commands behave quite differently. Here the commands:

```

rsync -av --del $SOURCE gianluca@10.10.11.47:/home/gianluca/ 

```

in this case it asks me for the password and then nicely show me only the update with respect to the existing files.

In the second case
```

rsync -av --del $SOURCE /media/TOSHIBA\ EXT/gianluca/

```
it always shows me at screen **all** the directories to be copied and it takes longer than the LAN-based backup.

What is the reason for this different behavior?

thanks in advance,
g.

---

### Post by The Cog on 2013-01-10
It might be this (from man rsync):
> --modify-window
              When comparing two timestamps, rsync treats the timestamps as being equal if they differ by no more than the modify-window value.  This is normally 0 (for an  exact  match),  but
              you  may find it useful to set this to a larger value in some situations.  In particular, when transferring to or from an MS Windows FAT filesystem (which represents times with a
              2-second resolution), --modify-window=1 is useful (allowing times to differ by up to 1 second).

---

### Post by sudodus on 2013-01-10
... and the speed difference may simply depend on slow writing speed to the external drive.

- Is it a USB 2 drive? -- slow transfer speed, if you connect via eSATA or USB 3 it will be much faster.

- Is it NTFS file system -- slow linux driver for NTFS, if you use a linux file system for example ext2, ext3 or ext4, it will be much faster.

---

### Post by g.a. on 2013-01-10
thanks to both, however

```

rsync -av --del --modify-window=10 $SOURCE /media/TOSHIBA\ EXT/gianluca/

```

(I tried from 1 to 10 seconds) did not change the fact that all the directories are listed

---

### Post by sudodus on 2013-01-10
> **g.a. said:**
> thanks to both, however

```

rsync -av --del --modify-window=10 $SOURCE /media/TOSHIBA\ EXT/gianluca/

```

(I tried from 1 to 10 seconds) did not change the fact that all the directories are listed
What file system is it on the disk containing the backup (/media/TOSHIBA)? If it is FAT or NTFS, you also have the problem, that permissions for files and directories are set, when mounted in linux. So maybe the problem is that the permissions are not the same, simply cannot be preserved.

If you are backup up system files of linux, please consider using a file system, that can conserve the permissions, otherwise a restored system might not work properly!

---

### Post by vanadium on 2013-01-10
This might very well be the cause: with the -a option, rsync also (tries to) update the permissions. If the destination file system does not support them, it would try each time and fail.

If converting to a file system that supports permissions is not desired, you should instead change your rsync option.

-a stands for -rlptgoD

In your case, you need -r (recursive), you don need -l (copy symlinks as links won work if the target file system does not support symlinks), you don't need -p (keep permissions), you want -t (preserve modification times), you don want -g nor -o (preserve group, owner) and probably you don't need -D as well (this is a technical option to transfer and recreate character and block devices). Your command may become:

```

rsync -rtv --del --modify-window=10 $SOURCE /media/TOSHIBA\ EXT/gianluca/

```

---

### Post by g.a. on 2013-01-11
thanks, I solved the issue.

The external hard disk was a NTFS type, so I partitioned in two by adding an EXT4 type and I used the original rsync command in the latter.

thanks again
g.

---

