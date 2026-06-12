---
title: "Hardrive Content Difference Checker - Transfer Confirmation"
date: 2013-11-21
forum: General Help
---

### Post by mkngl84 on 2013-11-21
I'm looking for a software package or similar or to create a simple program (by myself or someone) to:

- Compare the contents of two hard drives after file transfer (that was not a one to one copy).
- So, identical file locations are not required so long as an exact copy of each file is found - this would return nothing or identical match.
- I'm thinking this could be done with the help of the find and md5sum program.
- a databases could be created for each directory (where one of the hard drive's filesystems are mounted as subdirectories)
- each row would represent one file in the filesystem
- the first column could be the file location and the second the calculated md5sum of that file
- the/a program could then compare the two database files, cancel out identical md5sums, and print a log showing what and where files are that are not in both locations.

A backup program like rsync wouldn't work for this because of complicated differences in file locations between the two drives. I'm just looking to make sure all the data is copied and am curious if anyone knows if such a program exists.

Know of such a thing?

Thanks much,
M.

---

### Post by Bucky Ball on 2013-11-21
I check the size of the original folder with that of the backed up one after back up. 

Also, you can use something that does recursive backups. It checks if the file exists in the backup folder already. If not, it adds; if so and it's changed, it backs up. I use luckybackup myself. Works a treat, but there are lots of others that can sync the two locations so they ALWAYS remain identical. Must be careful not to get source and target mixed up with these though.

---

### Post by mkngl84 on 2013-11-22
Cool. Checking used space could help except for small files that may have not been copied for whatever reason such as having picked and chosen individual files and folders to transfer from the source drive to a new arrangement on the destination drive. I'm fairly sure I got them all and the idea for such a program came back to me. Before moving any files over, a simple command such as this, first, probably would have been best:
```
cp -av /source/* /dest/
```

I've been looking for a good backup app. I'll check it out.

---

