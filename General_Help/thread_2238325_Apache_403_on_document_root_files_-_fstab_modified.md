---
title: "Apache 403 on document root files - fstab modified - all document root 777"
date: 2014-08-07
forum: General Help
---

### Post by jona303 on 2014-08-07
Hello all,
I've installed LAMP on a fresh ubuntu installation. The thing is that i want to share my localhost with the one on the windows installation of the computer.

This directory is on a ntfs partition (d:/localhost on Win). I had a 403 and I suspected a permission issue, so searching the web I found that I had to change the fstab file.

I added this ( this is the last version with rwx for everybody):
```
/dev/sda3 /media/jona/datas ntfs auto,users,uid=1000,gid=1000,utf8,dmask=000,fmask=000 0 0
```

But I still have a 403 on my localhost files ([http://loalhost/client/file](http://loalhost/client/file)).

I suspect a user issue but I can't uderstand why, and how to solve it.

Can anyone help me ? 

Thanks

---

### Post by jona303 on 2014-08-07
Solved,
shame on me, it wad in the apache configuration (i didn't add my custom directory in apache2.conf :oops: )

---

