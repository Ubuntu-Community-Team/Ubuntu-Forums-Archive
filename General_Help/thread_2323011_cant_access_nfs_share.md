---
title: "cant access nfs share"
date: 2016-05-02
forum: General Help
---

### Post by eran_raz on 2016-05-02
Hi all.

we have several Ubuntu pc in our organization. thy all used to access a share on our storage. since yesterday or so most pf the except one cannot access this share anymore. from windows pc, the same users can access the share.

i tried to use the user from the computer who can access the share on the other Ubuntu pc - didn't work.

the only thing that changed in the last couple of days is the fact that we changed password to all of our user (Active Directory users).

does anyone have an idea what went wrong? any direction to check?

Btw - its an ntfs share, not nfs.

here is how i try to connect:

[http://s1227.photobucket.com/user/eranhuba/media/u2_zpslznzuovq.jpg.html?sort=3&o=1](http://s1227.photobucket.com/user/eranhuba/media/u2_zpslznzuovq.jpg.html?sort=3&o=1)

here is the error massage i get:

[http://s1227.photobucket.com/user/eranhuba/media/U3_zpsklkotw43.jpg.html](http://s1227.photobucket.com/user/eranhuba/media/U3_zpsklkotw43.jpg.html)

---

### Post by TheFu on 2016-05-02
Is this NFS or Samba?  Vastly different things.  The title and the words are confusing - please edit the original post and be very clear.

If samba, did you smbpasswd to match the new passwords?  We don't use AD here, so I don't know if that is required or not.  There are password-sync solutions.  Honestly, NFS is easier and you can use NFS to access the same storage from Unix-clients as you use samba to access from Windows.  I always, always, always, prefer NFS over Samba from Unix.

If samba, please run and post the output from **testparm**.

Can't see photos. Sorry.

---

### Post by eran_raz on 2016-05-03
i stated "BTW - its an ntfs share, not nfs." - i cant change the headline, just the body of the massage, that's why i added this line, to clarify.

so as i said, the share is ntfs share, not nfs.

ill check your suggestions and update the thread.

---

### Post by eran_raz on 2016-05-03
just noticed the ubuntu that do work uses samba 4.1.6, the others who's on them the share dosnt work use samba 4.3, do im fuessing its a bug in the 4.3 version.

---

