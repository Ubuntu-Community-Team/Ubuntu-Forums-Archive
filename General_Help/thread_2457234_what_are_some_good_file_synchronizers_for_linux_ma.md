---
title: "what are some good file synchronizers for linux? maybe Grsync?"
date: 2021-01-28
forum: General Help
---

### Post by ronjjjg8885 on 2021-01-28
thanks!

---

### Post by ajgreeny on 2021-01-28
For what purpose?

Tell us much more if you want a good answer.
You can start playing with rsync which is a default install in the system so read through the manual ```
man rsync
``` to see details.
You can easily install grsync if you need which is a simple GUI front end to rsync.

---

### Post by TheFu on 2021-01-28
I use rsync 99% of the time.
I use nextcloud 1% of the time.

If I'm sync'ing the same stuff over and over, I'll create an rsync script for that specific purpose.  Some rsync script names:
[LIST]
[*]quicken-backup-to-romulus
[*]/d/D1/sync-M_T_R_X-on-istar
[*]push_keepass_db
[/LIST]
Guess what they each do?

Here's what /d/D1/sync-M_T_P_B-on-istar has:
```
#!/bin/bash 

if [ "istar" != "$HOSTNAME" ] ; then
  echo "Wrong host: $HOSTNAME "
  echo "Run on hostname istar "
  exit 1;
fi

EXCLUDES="--exclude **/.Trash* --exclude lost+found --exclude ZCS-2012"

ionice rsync -av --stats --progress $EXCLUDES --delete /d/D1/ /d/b-D1/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D2/ /d/b-D2/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D3/ /d/b-D3/

```
The hostname check is needed because the location of this script is on NFS storage and I'll forget that /d/b-D? isn't available on those other machines. This is a local-to-local storage copy.

*push_keepass_db* script ensures my encrypted password DB has multiple copies on about 6 systems. This is a local-to-remote copy. ssh-keys are used.

---

### Post by yaminb on 2021-01-28
As other's have said, it's really going to depend on your use case.

I thought I'd be doing a lot of sharing between my Windows and Ubuntu drives, but I really don't.
As I had converted from mainly windows to Ubuntu, I just kept using my MS OneDrive account for my personal files.

To get those files onto Linux, there's a synching program called onedrive --monitor. That syncs my OneDrive account to my Ubuntu install. it's worked reliably well. I haven't tried editing a file at the same time on both drives, but for my purposes it works beautifully. 
So now, i have most of my 'personal files' backed up in 3 places (Windows, Linux, One Drive).

For larger files, I have a local NAS that I use to store things as well. Yet again, my personal use case is here. I just store these files directly on the NAS, which uses its own software to backup. Rarely do I need the speed of local processing of these kinds of files (pictures, videos...). If I do, i quickly copy it over, edit, and copy it back.

As others have said. What do you want to do!?

---

### Post by ronjjjg8885 on 2021-01-29
hi
at the end i've used Grsync
im just synching photos and videos of two hard drives. one of them is external...
how can u use Grsync's gui to check if all the files were transfered well? is there a compare feature in it?
thanks!

---

### Post by TheFu on 2021-01-29
Checking files is easy with rsync, but most of the time, just run the process again and see there aren't any changes. 
No clue about grsync. Found it much too cumbersome to deal with. Maybe the grsync manpage can help?  
[http://manpages.ubuntu.com/manpages/focal/man1/grsync.1.html](http://manpages.ubuntu.com/manpages/focal/man1/grsync.1.html)

Wow. That's just useless.  Another reason to stick with rsync.

---

### Post by ajgreeny on 2021-01-29
It's a long while since I used grsync, though it used to be my go-to application for this purpose.

However, I do recall that re-running the same action or session will quickly show that nothing was transferred if all is well; it is something I used simply to check when I first started using grsync.

As I said in my first post above grsync uses rsync in the background so mostly what it does amounts to the same activities though rsync probably has many more command line options you can invoke if compared with grsync.

The man page for grsync is pointless and I think largely depends on the rsync manual so read that carefully.

---

### Post by ronjjjg8885 on 2021-01-30
thank you people

---

