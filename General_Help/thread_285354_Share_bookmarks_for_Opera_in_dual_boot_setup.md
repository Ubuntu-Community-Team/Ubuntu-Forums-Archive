---
title: "Share bookmarks for Opera in dual boot setup"
date: 2006-10-26
forum: General Help
---

### Post by Oki on 2006-10-26
Hi

I am dual-booting with Windows xp and Ubuntu Dapper Drake. I have one disk in Fat32, so both os can read/write to it. In this disk I have saved the profile for FF and Thunderbird, and it works very vel. But, how can I do that with bookmarks belonging to Opera? Meaning; I want to share the same bookmarks for Opera in Windows and Opera in Linux. 

Thanks for all help

---

### Post by Oki on 2006-10-27
Perhaps this works:
[http://forums.pcworld.co.nz/archive/index.php/t-63844.html](http://forums.pcworld.co.nz/archive/index.php/t-63844.html)

---

### Post by bailout on 2006-10-28
Bookmarks are easy to share and you can also do the same with many other settings eg notes, contacts, mail, but some are more difficult to set up. What I do is have my windows opera installed on my shared fat32 partition. If you install it to there and select 'no' when it asks you whether you want to enable more than one profile, it will store all your profile date in the Opera install folder on the shared drive. 

Once you have that set up then to use the same bookmark file for both just open opera in Linux, go Bookmarks->Manage Bookmarks and then file->open and navigate to your bookmarks on the fat32 drive and select.

For more info on this read my thread on the Opera forums.

[http://my.opera.com/community/forums/topic.dml?id=128708](http://my.opera.com/community/forums/topic.dml?id=128708)

---

### Post by Oki on 2006-10-28
Thank you for your help:D

---

### Post by maheshjagadeesan on 2006-10-31
> **bailout said:**
> Bookmarks are easy to share and you can also do the same with many other settings eg notes, contacts, mail, but some are more difficult to set up. What I do is have my windows opera installed on my shared fat32 partition. If you install it to there and select 'no' when it asks you whether you want to enable more than one profile, it will store all your profile date in the Opera install folder on the shared drive. 

....

The bookmark tip is a good one, but I think I have an easier solution, not only for sharing bookmarks, but for sharing almost everything else. 

You can [see it here]("http://my.opera.com/community/forums/topic.dml?id=128708&t=1162277522&page=1") in the Opera forums.

Note: if your settings are on an NTFS partition, then you are not out of luck - simply install the ntfs-3g package (or the ntfs-fuse package as recommended in the [Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")), and go ahead.

HTH :)

---

