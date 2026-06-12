---
title: "Disk space problem"
date: 2006-12-16
forum: General Help
---

### Post by radiors on 2006-12-16
Hello,

I have searched the forums but have not found an answer to this.

There is a difference between my disk space that is available vs. not used.  How do I get them to be both the same?

Here is my df:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              59G   55G  1.3G  98% /
varrun                252M  164K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hda1             6.9G  5.7G  1.2G  84% /media/hda1
/dev/hda5              82G  428M   82G   1% /media/hda2

I have also attached a screen shot of my Monitor.

This may be a separate problem, but I lost a lot of disk space on my Linux partiton when I tried to make a backup archive but ran out of disk space when the archive got to 14 Gigs before it was completed.  I had to go into recovery mode and delete the backup in order to even reboot to the GUI.  All the disk space used by the  backup archive was not recovered after I deleted it in recovery mode.  I should have about 14 gigs free.

I have a feeling I have a big file remnant I can't find. 

Any ideas?  Thanks

---

### Post by Topsiho on 2006-12-16
It is a guess, but after you deleted the stuff, did you delete the trashbin too?
For if the big file still is in the trash then it still occupies diskspace ...

Topsiho

---

### Post by radiors on 2006-12-16
Thanks.

Yes, I have emptied the trash bin.

But, glad you asked.  Sometimes you miss the obvious stuff.

---

### Post by bapoumba on 2006-12-16
Hi,

```
du --summarize --human-readable   *
```
will list the total directories or files in the current directory

```
du -ah | sort -rn | head
```
will list the top few biggest directories in the current one. Skip the **| head** if you want the complete output.

I think [baobab]("http://www.marzocca.net/linux/baobab.html") could also help you find what is taking up space.
I used to use it with dapper (universe repos), but I cannot find it in edgy packages :/

---

### Post by bettlebrox on 2006-12-16
How did you delete the backup?

---

### Post by radiors on 2006-12-16
Problem solved!!!

Baobab did the trick.  I found a hidden .Trash folder in the root directory that had the whole 14 Gig backup file in it.  This did not show up in the standard search even when I included hidden files in the search parameters.

It turns out the first poster was also on track.  He asked, did I empty the trash.  Well, I thought I did.  But, I guess there was one more step.

Thanks to everyone!  Linux and this group are fantastic.  I'd bag my Windows partition completely but I need it to run my flight planning software.  Runs like a snail in Vmware.

---

