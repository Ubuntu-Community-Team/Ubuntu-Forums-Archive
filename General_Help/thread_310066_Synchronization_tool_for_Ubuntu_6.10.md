---
title: "Synchronization tool for Ubuntu 6.10"
date: 2006-11-30
forum: General Help
---

### Post by Thumper322 on 2006-11-30
Hello all,

Is there some kind of synchronization tool available for Ubuntu? Under Windows XP, I used [SyncToy]("http://www.microsoft.com/windowsxp/using/digitalphotography/prophoto/synctoy.mspx") quite avidly. I need both "Echo" and "Synchronize" functions. I use "Echo" for incremental backups, and "Synchronize" to synchronize project folder on my computer with a work share.

I believe **rsync**, from what I've heard, can take care of "Echo"; but can it, or some other tool, deal with "Synchronize"?

Thanks for any help.

---

### Post by Oki on 2006-11-30
I to want a program like synctoy - hope someone can answer:-)

---

### Post by Thumper322 on 2006-11-30
D'oh! I should've thought to search through the forums. ](*,)

[This topic]("http://www.ubuntuforums.org/showthread.php?t=223571") seems to answer the question. Apparently the tool of choice is "UNISON," available as "unison" and "unison-gtk."

---

### Post by wieman01 on 2006-11-30
Just to reconfirm what you have just found out:

>> [COLOR="Red"]"rsync"[/COLOR] for incremental backups 
>> [COLOR="Red"]"unison"[/COLOR] for synchronizing 
>> [COLOR="Red"]"partimage"[/COLOR] for system backup

I am using both. "unison" is really handy when it comes to synchronizing emails, bookmarks, personal files, etc. I am using "rsync" twice a month to pull full backups of my personal files & folders. 

Then I do monthly backups using "partimage". A guide can be found here: [http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522")

---

### Post by Thumper322 on 2006-12-01
> **wieman01 said:**
> Just to reconfirm what you have just found out:

>> [COLOR="Red"]"rsync"[/COLOR] for incremental backups 
>> [COLOR="Red"]"unison"[/COLOR] for synchronizing 
>> [COLOR="Red"]"partimage"[/COLOR] for system backup

I am using both. "unison" is really handy when it comes to synchronizing emails, bookmarks, personal files, etc. I am using "rsync" twice a month to pull full backups of my personal files & folders. 

Then I do monthly backups using "partimage". A guide can be found here: [http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522")

Thanks, wieman01. I've got Unison set up nicely, and once I figure out how to write to NTFS filesystems with Ubuntu, I'll start using rsync for backups.

---

