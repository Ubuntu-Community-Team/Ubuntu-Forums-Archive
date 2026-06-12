---
title: "rsync error (5)"
date: 2020-06-18
forum: General Help
---

### Post by raccoonstrait on 2020-06-18
Hello Everyone,

Xubuntu 20.04. I am getting an rsync error (5) and that it is "skipping any contents form this failed directory" for some of the files on a very large NTFS USB connected drive. I actually have 4 drives, all the same brand and size, 2 of which are primary and 2 of which are backups. On one set rsync works fine, the other set is where the issue seems to be, and it seems to be a read issue, rather than a write issue.

My research into these errors say that it is one of three things:

1. Disk Error
2. Insufficient privileges
3. File lock by antivirus program

In response to the first issue the drive has been connected to a Windows machine and ran chkdsk, and if there were errors, those errors were corrected.

In response to the second issue I found that there were some odd group and user name issues, which I have corrected via fstab.

The only antivirus I have is Clam and the error (5) problems effect only a few of hundreds of files. 

Those files are mp3's and they play, so I am thinking that it isn't a corruption issue, but I have been wrong before. I just tried to copy one of the affected folders into a new one, then deleted the original and ran rsync again. The error did not go away. I then tried renaming the target folder and re-ran rsync.

OK, I created new folders and copied the content from the error folders to new folders then deleted the original folders and renamed the new folders. Problems not solved.

Any other ideas?

Raccoon Strait

---

### Post by #&amp;thj^% on 2020-06-18
Please include your command used.
This might be helpful
Example with flags only. (Do Not use as a command only path and directory needed)
```
rsync -rPz
```

---

### Post by raccoonstrait on 2020-06-18
Here you go:

```

rsync -r -t -p -o -g -v --progress --delete --ignore-existing -s /mnt/mydrive02 /mnt/mydrive02-BU

```

---

### Post by raccoonstrait on 2020-06-20
I have done some more checking and since the permission error was solved and anti-virus has not impacted the other drives that do the same process, I looked more into disk errors. This is an SSD drive, and I had just reformatted it due to disk error, using gparted to NTFS, which it was before. Then I got the above errors. So I dismounted this drive, rebooted my other machine to Windows and did chkdsk again. I got errors, and after repeated attempts to repair those errors chose to reformat the drive again, this time using Windows. I elected to not use the Fast Format option and after many hours (it is a 4 TB drive) got a message from Windows that it could not complete the format.

Oh well. New drives being ordered, this time 4TB HDD rather than SSD. Marking this solved.

Raccoon Strait

---

### Post by sudodus on 2020-06-20
Did you check the S.M.A.R.T. information of the problematic drive? If not, you can do it fairly easily according to the following link,

[S.M.A.R.T. information of HDD and SSD](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors/972983#972983)

If it is good, you might revive it with a new partition table, otherwise you lost it.

---

