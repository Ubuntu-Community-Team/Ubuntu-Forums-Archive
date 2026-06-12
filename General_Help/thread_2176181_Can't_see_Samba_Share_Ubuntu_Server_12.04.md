---
title: "Can't see Samba Share Ubuntu Server 12.04"
date: 2013-09-23
forum: General Help
---

### Post by jeff27 on 2013-09-23
I've been playing around with Ubuntu 12.04, both server and desktop for a couple weeks now so not much experience.  Here is my home setup.

One laptop running Ubuntu 12.04 Desktop
One laptop running Windows XP
One server running Ubuntu 12.04 Server running Samba

I'm able to see the shared folders with the XP laptop but can sometimes see them with the Ubuntu Desktop. Any idea what I need to change or what I'm doing wrong?

---

### Post by Morbius1 on 2013-09-23
Without getting into the muck of samba settings the easiest thing to do is rely on the fact that all Linux ( and OSX ) machines can communicate with each other using an mDNS qualified host name.

On the Ubuntu laptop open a terminal and type:
```
nautilus smb://hostname.local
```
[COLOR=#0000cd]*Change "hostname" to the hostname of the Ubuntu server.*[/COLOR]

When it opens nautilus to that location bookmark it: Bookmark > Add Bookmark. You can rename the bookmark if you desire.

---

### Post by jeff27 on 2013-09-23
When I type this in it returns "Could not display, error failed to return share list" :  ```
nautilus smb://ubuserv.local
```

When I type ```
nautilus smb://ubuserv
``` it brings me to the list of shares which is great.

Forgive me but I'm really new at this.  Am I to literall type it .local or should I be replacing that as well?

---

### Post by Morbius1 on 2013-09-24
If you can access it by "ubuserv" alone that's fine - that's the way it's supposed to work.

Something must be wrong with the avahi service or the port it uses on either the server and/or the client that's preventing accessing it by ubuserv.local.

---

