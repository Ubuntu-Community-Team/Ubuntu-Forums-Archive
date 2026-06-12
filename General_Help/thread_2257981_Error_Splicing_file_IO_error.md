---
title: "Error Splicing file: I/O error"
date: 2014-12-23
forum: General Help
---

### Post by wenger828 on 2014-12-23
So forgive my noobiness, I am by no means a computer expert but good enough to manage to get my failing harddrive readable via Ubuntu testdisk.  I had an issue with a drive failing (1200+ bad sectors), caused windows to just hang up as it was loading at the splash icon.  Running ubuntu via CD and got the disk readable via testdisk and was able to get it to rewrite the tables (i don't know what the exact term is).  it allowed me to mount the drive to be able to read the files.  i formatted a new 2TB disk in windows, shtu down the computer, hooked up the new drive & bad drive and booted ubuntu back up in hopes that i can drag and drop all of my important files over (i make music as a hobby.. have hours and hours of songs that i've made that i would really hate to lose). Issue i'm having is that randomly, some files will not copy over due to a I/O error/error splicing file.  Can someone point me in the right direction? What i'm doing is clicking the entire folder and copy & paste to the new disk, i noticed that if i took that individual file and dragged it over it would sometimes copy over.  I could also play some of those files.  it would be really hard for me to find out which individual file out of the thousands i have that wouldn't copy over.  some one please help!!

---

### Post by r.stiltskin on 2014-12-24
First of all, with a failing drive you should avoid writing anything to that old disk and don't do anything to try to fix the files on that disk (since any "repairing" is going to involve writing to the disk), at least until after you have copied as much as possible to the new disk.

You didn't say anything about how you partitioned the drives, so for the moment I'll assume that each drive was formatted as a single partition.  Correct me if I'm wrong.  With both of them mounted in Ubuntu, you have to determine exactly where they are mounted in Ubuntu's file system, and then you can use rsync to copy your files from the old disk to the new one.  I believe that rsync will continue copying whatever it can read even if it encounters errors in some files.

Open a terminal window and run this command:
```
ls -l /media/ubuntu
```
and post the output.  That should let us identify the mountpoints of the two mounted disk partitions.

(I don't have an Ubuntu CD available but I'm pretty sure they will appear under /media/ubuntu.  If not, we'll figure it out from the output of that command.)

---

### Post by wenger828 on 2014-12-24
r.sstiltskin - thank you for the reply.  i wasn't actually writing anything to the old disk, i was trying to simply copy & paste the files over from the old to the new.  i don't know the terms well (i work on cars for a living, not computers) but i did whatever testdisk does after it's done analyzing the disk.  i will run that command and report back the moment i get back home, thank you

---

