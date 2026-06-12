---
title: "Upgrade to 13.10 broke Roundcube web access"
date: 2014-04-30
forum: General Help
---

### Post by networkguy09 on 2014-04-30
I get the following when I go to my website [https://website.com/roundcube/](https://website.com/roundcube/)

```
DATABASE ERROR: CONNECTION FAILED!
Unable to connect to the database!
Please contact your server-administrator.
```

I don't see anything indicating a problem in /var/log/mail.log

I went through and redid dpkg-reconfigure roundcube-core

Checked
/etc/dbconfig-common/roundcube.conf and /etc/roundcube/debian-db.php and they have the correct sql settings

Mail is working through my mail client applications. I just cannot access the web gui.

Did some searching for this on the forum and found a few posts with no replies and thread closed by the moderator. Any help is appreciated.

---

