---
title: "Need help with internet connection hang up"
date: 2007-01-10
forum: General Help
---

### Post by maranellored on 2007-01-10
i'm a linux newbie. I'm using Xubuntu edgy.
My problem is that, after a while, my browsers(opera and FF) both terminate my browsing after a while but my downloads and IM programs work fine. It seems like only the browsers cannot access the internet. Heres the output from the /var/log/messages file

```
Jan 10 20:57:58 mRED gconfd (root-8761): starting (version 2.16.0), pid 8761 user 'root'
Jan 10 20:57:59 mRED gconfd (root-8761): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 10 20:57:59 mRED gconfd (root-8761): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 10 20:57:59 mRED gconfd (root-8761): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 10 20:57:59 mRED gconfd (root-8761): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 10 20:57:59 mRED gconfd (root-8761): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 10 20:58:59 mRED gconfd (root-8761): GConf server is not in use, shutting down.
Jan 10 20:58:59 mRED gconfd (root-8761): Exiting
Jan 10 20:59:56 mRED gconfd (root-8789): starting (version 2.16.0), pid 8789 user 'root'
Jan 10 20:59:56 mRED gconfd (root-8789): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 10 20:59:56 mRED gconfd (root-8789): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jan 10 20:59:56 mRED gconfd (root-8789): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 10 20:59:56 mRED gconfd (root-8789): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 10 20:59:56 mRED gconfd (root-8789): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 10 21:00:26 mRED gconfd (root-8789): GConf server is not in use, shutting down.
Jan 10 21:00:26 mRED gconfd (root-8789): Exiting
```

PLEASE HELP !!!

---

