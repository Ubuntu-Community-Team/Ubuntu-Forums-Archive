---
title: "rsync - since changing name of external HDD rsync wants to copy everything again !"
date: 2018-05-30
forum: General Help
---

### Post by freeflyjohn on 2018-05-30
I used grsync to back up (mirror) an internal HDD on my server to an external USB HDD.

The files were successfully copied (mirrored) to the external HDD and as I wanted it to be a mirror of the internal HDD I enabled the option 'Delete on destination'.

Once it had copied all the files I tested grsync to make sure it mirrored any files I changed on the internal HDD (e.g. add new files / remove deleted files).

 It was all working well until I renamed the external HDD, since then grsync wants to delete all the files and copy them all over again.  

So I stopped the process as it took 10 hours last time (1.5TB) and I dont want to have to repeat the process purely because I changed the name of the external HDD.

The original paths were:

Source: /media/plex/ 
Destination: /media/MyElements/

I then renamed the external HDD from MyElements to plexbackup:

Source: /media/plex/ 
Destination: /media/plexbackup/

Only the external HDD name has changed, the folders and files are exactly the same.  So why does rsync now try to delete everything on the external HDD and copy it again ?

---

### Post by TheFu on 2018-05-30
It shouldn't if the underlying rsync command is modified in a consistent way and the timestamps are correct.
If you can post the old rsync command, it should be clear what the new one should be.

One odd thing about rsync is that sometimes it is faster to re-copy the files over than perform the magic block-level diffs.  This never happens for network syncs, but for local (on the same system), it can.  There are options to force a timestamp check only, but this works if if the source/target are consistently setup.

There is a test-mode for rsync which shows what would happen without the actual copies. 

I've never used grsync.

---

### Post by leunam12 on 2018-05-30
Also post the result of lsblk (with the external HDD plugged in).

---

### Post by freeflyjohn on 2018-05-30
Thanks for the replies - I've just reformatted the external HDD and started rsync all over again so I will see how that goes (seemed the easiest solution)

---

### Post by rbscycle on 2018-08-20
GRSYNC won't run on Ubuntu 18.04.1 LTS.  No error message.  If I copy the 'rsync' command from 'grsync' to a terminal window it executes flawlessly. 
I trashed the system.  reformat HDD. Re-installed Ubuntu 18.04.01.  No change, still won't run.  No error message.  Copy & Paste the grsync command line to terminal, it runs fine.

---

