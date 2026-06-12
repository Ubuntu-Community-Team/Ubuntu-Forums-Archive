---
title: "rsync stopped deleting unwanted files in target"
date: 2014-03-21
forum: General Help
---

### Post by vasa1 on 2014-03-21
I had things set up properly but suddenly I'm seeing something odd ...

This is the command I run:
```
rsync -lrtv --delete --protect-args --modify-window=1 --files-from=/home/vasa1/Dropbox/rsync-include.txt / "/media/vasa1/TOSHIBA EXT/BACKUP/" &> rsync.log

```
I've been using **--delete** to remove files from the backup device when they're no longer present in the source.
Then, just to reassure myself, I would run diffqr (my alias for **diff -qr /home/vasa1/Desktop /media/vasa1/TOSHIBA\ EXT/BACKUP/home/vasa1/Desktop**). It would always return the prompt but today I noticed that there is output like this:
```
[02:35 AM] ~ $ diffqr
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop: aaa.txt
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop: allhistory.log
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop: bookmarks.html
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: about_config.txt
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: bm1
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: from troubleshooting
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: Mar19::170535.png
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: patterns.ini
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: sorted.txt
Only in /media/vasa1/TOSHIBA EXT/BACKUP/home/vasa1/Desktop/FxSettings: stylish20140302.txt
...

```I don't know why files that I've deleted from source remain in the target destination even though I'm using "--delete".

Any pointers will be most appreciated!

---

### Post by vasa1 on 2014-03-21
I created the problem myself.

Today, I changed from the Aurora channel to the beta channel of Firefox. I did a little housekeeping to reflect that but inadvertently retained a reference to a now non-existent folder in the "includes" list looked at by rsync.

Removing that folder brought things back on track.

---

### Post by andygmorris on 2014-05-09
> **vasa1 said:**
> I created the problem myself.

Today, I changed from the Aurora channel to the beta channel of Firefox. I did a little housekeeping to reflect that but inadvertently retained a reference to a now non-existent folder in the "includes" list looked at by rsync.

Removing that folder brought things back on track.


@vasa1: Well spotted, and well noted here too. Thank you!!

I noticed this issue too when I was distro-hopping and that my self-written rsync backup routine wasn't deleting files that should be deleted during the rsync with delete and delete-during flags.

Personally, I consider this a (logic) fault in rsync and I will try and follow up with the developers to see how this can be better 'noticed' by the users of rsync in this kind of situation.

Again, well spotted!

---

