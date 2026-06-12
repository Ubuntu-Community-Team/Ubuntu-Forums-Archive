---
title: "Directory disappears"
date: 2008-03-01
forum: General Help
---

### Post by odorikakeru on 2008-03-01
Something strange happened to me (well, my system) last night.

about a week ago formatted a software RAID (striped) using mdadm, and I have been using it as a store for larger files with no problems until the early hours of this morning.

Suddenly one of the directories just disappeared and it took me completely by surprise. I had been using a BitTorrent client to download in the background and it started flagging up errors that the data was missing.

I have since remounted, run fsck, and I even checked .Trash (just in case), but as I'm not very good at this sort of thing I don't know what else to do. My system keeps telling me that there aren't any problems.

The only hint that something isn't right is when I check Properties in Nautilus. the sum total of all the files is 338.6Gb, whereas the "Used:" below reads 375.8Gb. But I'm not getting the "Some contents can't be read" message (I'm paraphrasing as I can't remember the exact wording) in the Properties panel which I would expect if there was a corrupted directory.

Can anybody point me in the right direction?

&#33310;&#39366;

---

### Post by Shazaam on 2008-03-01
Have you looked in root's .Trash folder?
```
gksudo nautilus
```
****Warning**** Using this code gives you ABSOLUTE root access to EVERYTHING. Be careful.
Hit Ctrl+h to show hidden files and then browse to the /root/.Trash folder.

---

### Post by odorikakeru on 2008-03-02
Thanks, I should've thought of that one.

Unfortunately, there weren't any relevant files in /root/.Trash, and on the array itself the .Trash-root folder hasn't been created yet.


Can I send out an appeal to anyone who can recommend any FS checking programs, or file recovery programs which might be useful at a time like this?

I forgot to mention, the raid is formatted to ext3 with no fiddles or tweaks (I had been tempted by the idea of ext4 and extents, but gave it a miss in the end).

&#33310;&#39366;

---

### Post by odorikakeru on 2008-03-02
Update....

I have run ```
sudo e2ls -D /dev/md0
``` and it returned a directory list containing my missing folder marked as being deleted (with >[folder]<)

Now, this is an ext3 file system so the usual undelete utilities aren't working (yes, in desperation I downgraded to ext2 through tunefs and gave them a try anyway, but to inodes have been wiped). Also, there are maybe 40 or so files, mostly binary (video) and rather large, so using grep isn't really an option... unless someone knows otherwise.

Am I giving up these files as lost or is there anything else I can try?

BTW, it's stil a mystery how all this started in the first place, it would be helpful in the future to find out.

---

