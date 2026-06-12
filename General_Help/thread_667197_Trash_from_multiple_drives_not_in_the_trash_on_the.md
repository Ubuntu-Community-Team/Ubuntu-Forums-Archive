---
title: "Trash from multiple drives not in the trash on the panel?  Only trash from / ."
date: 2008-01-14
forum: General Help
---

### Post by Mysticle31 on 2008-01-14
This is interesting..

I have multiple hard drives:

I have two WD Raptors in a linux RAID 0 array as /

I have a 20 gig and a 40 gig LVM together to be my TV drive, where mythtv stores it's recordings.  100MB of the 20 gig (as it's primary master) is my /boot.

I have a 250 gig data drive mounted as /media/data

I have a 500 gig WD My Book mounted as /media/My Book 

every drive has it's own .Trash folder

/  is in  ~/.Trash
/media/data is in /.Trash-steve  (/media/data/.Trash-steve)
/media/My Book is in /.Trash-steve (/media/My Book/.Trash-steve)
And I lied, TV drive doesn't have one.


Anyhow,

When I delete something on a hard drive the file goes to it's respective trash folder.  For example if I delete a folder on my data drive called BLAH it will go into /media/data/.Trash-steve/BLAH 

However, "trash:" only displays the trash of / and not the other drives.  I can empty the trash and still have stuff in the other trash folders that I have to go delete manually by deleting everything in the .Trash-steve folders.

Isn't that interesting?  How do I fix it?

---

### Post by erpo on 2008-01-14
I've had this problem too. It's a bug. The reason for having multiple trash folders is that moving files between filesystems takes much longer than moving files within filesystems. Gnome sometimes forgets about the trash folders on other filesystems.

If you want, you can file a bug report at bugzilla.gnome.org.

For now, delete the files from a console.

---

