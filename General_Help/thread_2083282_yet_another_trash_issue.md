---
title: "yet another trash issue"
date: 2012-11-12
forum: General Help
---

### Post by agrayray on 2012-11-12
I think what happened originally was that I deleted the directory where this one vmware file was so it failed when emptying the trash...its on a USB drive

regardless I have had a file stuck in my trash for quite a while now...

Getting the "Failed to delete item from Trash" from nautilus  even with gksu nautilus etc...

Can not copy or move..get the same error...

from command line this is what happens, rm doesnt work, mv doesnt work, cp works and I can delete copy, can not delete any of the directories...can someone please advise on how I can remove the trash folder and or file?

Below is my terminal session:


rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ pwd
/media/TOSHIBA EXT/.Trash-1000/files

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ ls -la
total 276
drwx------ 1 rlintner rlintner  12288 2012-11-12 02:44 .
drwx------ 1 rlintner rlintner    248 2012-11-12 02:27 ..
-rwxrwxrwx 1 rlintner rlintner 327680 2012-07-29 19:05 Microsoft

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ sudo rm -rf Microsoft 

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ ls -la
total 276
drwx------ 1 rlintner rlintner  12288 2012-11-12 02:44 .
drwx------ 1 rlintner rlintner    248 2012-11-12 02:27 ..
-rwxrwxrwx 1 rlintner rlintner 327680 2012-07-29 19:05 Microsoft

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ mv Microsoft msSucks
mv: cannot move `Microsoft' to `msSucks': No such file or directory

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ cp Microsoft msSucks
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ ls -la
total 340
drwx------ 1 rlintner rlintner  12288 2012-11-12 02:52 .
drwx------ 1 rlintner rlintner    248 2012-11-12 02:27 ..
-rwxrwxrwx 1 rlintner rlintner 327680 2012-07-29 19:05 Microsoft
-rwxrwxrwx 1 rlintner rlintner 327680 2012-11-12 02:52 msSucks
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ rm msSucks 
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ ls -la
total 276
drwx------ 1 rlintner rlintner  12288 2012-11-12 02:53 .
drwx------ 1 rlintner rlintner    248 2012-11-12 02:27 ..
-rwxrwxrwx 1 rlintner rlintner 327680 2012-07-29 19:05 Microsoft

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ rm Microsoft 
rm: cannot remove `Microsoft': No such file or directory

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ cd ..
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000$ pwd
/media/TOSHIBA EXT/.Trash-1000
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000$ ls -la
total 16
drwx------ 1 rlintner rlintner   248 2012-11-12 02:27 .
drwx------ 1 rlintner rlintner  4096 2012-11-12 02:33 ..
drwx------ 1 rlintner rlintner    48 2012-11-12 02:50 expunged
drwx------ 1 rlintner rlintner 12288 2012-11-12 02:53 files
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000$ sudo rm -rf files/
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000$ ls -la
total 16
drwx------ 1 rlintner rlintner   248 2012-11-12 02:27 .
drwx------ 1 rlintner rlintner  4096 2012-11-12 02:33 ..
drwx------ 1 rlintner rlintner    48 2012-11-12 02:50 expunged
drwx------ 1 rlintner rlintner 12288 2012-11-12 02:53 files
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000$ cd files
rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ ls -la
total 276
drwx------ 1 rlintner rlintner  12288 2012-11-12 02:53 .
drwx------ 1 rlintner rlintner    248 2012-11-12 02:27 ..
-rwxrwxrwx 1 rlintner rlintner 327680 2012-07-29 19:05 Microsoft

rlintner@rlintner-laptop:/media/TOSHIBA EXT/.Trash-1000/files$ echo "I AM LOST, CAN SOMEONE HELP ME?"
I AM LOST, CAN SOMEONE HELP ME?

Thanks in advance!

---

### Post by agrayray on 2012-11-13
I solved this..sadly simply by booting into a windows os and deleting the trash folder from there....

I still would be curious to know why this happened incase it ever happens again.

but I am all set and fixed now.

---

