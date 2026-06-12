---
title: "MDADM/Samba/Ext4 video corruption issue"
date: 2012-12-08
forum: General Help
---

### Post by WhiskeyAlpha on 2012-12-08
Hi,

Im running Ubuntu 12.04.1 LTS as the OS on my main media file server at home.  It has a 6 x 2TB Raid 5 array (mdadm) that I use to house backups of my music and movies, which in turn I am able to stream to various playback devices around the house (samba).

This has been working like a dream ever since it was set up. However, I recently noticed a problem with video corruption in some of the more recent rips I've made.  My first investigation was with the application forums:

[http://www.makemkv.com/forum2/viewtopic.php?f=8&t=5766&p=24173#p24173](http://www.makemkv.com/forum2/viewtopic.php?f=8&t=5766&p=24173#p24173)

In summary: 

If I perform the whole ripping process locally, no errors occur.  The "glitches" are introduced even by a simple samba file copy from a Win 7 box to the Ubuntu file server.  

I can reproduce this, with one file in particular returning a different MD5 hash every time I copy it over to the Ubuntu box (though total byte count is always correct). Local copies result in a file with an identical MD5 hash 100% of the time.  I also attempted copying the file using SCP instead of samba and the resulting file still produced a bad MD5 hash.

Therefore, I assume there must be an issue with either the underlying RAID array (mdadm), file system (ext4) or sharing mechanism (samba/scp).

Can anybody advise some troubleshooting steps that might help me track down the culprit?

Thanks in advance :)

---

