---
title: "hubackup + external usb drive w/ntfs par = no dice"
date: 2007-12-17
forum: General Help
---

### Post by kefurd06 on 2007-12-17
so i'm trying to use hubackup with my external usb drive, which has a full 100 gig ntfs partition. hubackup will backup to my vista ntfs partition (internal), but not my external. skips the entire process and goes to 'let's check and see if it worked' which of course fails. any ideas? other backup solutions?

---

### Post by Bruce M. on 2008-01-27
> **kefurd06 said:**
> so i'm trying to use hubackup with my external usb drive, which has a full 100 gig ntfs partition. hubackup will backup to my vista ntfs partition (internal), but not my external. skips the entire process and goes to 'let's check and see if it worked' which of course fails. any ideas? other backup solutions?

Try something else, I just went through a horror story trying to us HURestore - it simply does NOT load.

HUBackup did make the backups - very slowly I might add - and I have to find an alternative way to restore using DAR!

Therefore **HUBackup** is not a good choice.

I'll be back with more info.
Bruce

---

### Post by Bruce M. on 2008-01-29
> 
Restoring File Using HUBackup

After receiving quite some emails about folks bewildered by the crashing hurestore I think it's only fair to create a post about how to restore files from archives created using hubackup using the underlying archiver , DAR.

Usually after a typical run of hubackup you will have two resulting files:

.hubackup-data/paepp-master-archive.1.dar
.hubackup-data/paepp-master-catalog.1.dar

(Thanks goes to Peter Päppinghaus for sending me an email about this)

To restore , which actually usually means extract in DAR's language you need to do something like:

dar -x .hubackup-data/paepp-master-archive -R TARGET_DIR

If there is more then one slice DAR knows how to switch between them properly.

That should be enough for most of operations, for more detailed explanation of what dar can do in restoration (or backup for that matter) DAR's manual pages are quite good.


One thing I didn't allow it to do was create backups in the /home folder. Which to me makes sense, because if you loose the /home folder, you loose the backups too.

HUBackup uses by default; ~/.hubackup-data/
~ = /home
/.hubackup-data = hidden folder ( the . )

So I put my backups on my second drive (another partition would be good) like this:

 /backups/24Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

This code worked for me when HURestore didn't work:

```
sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home/bruloo -wa -v
```

---

