---
title: "Failed to receive repository information"
date: 2012-12-16
forum: General Help
---

### Post by tehforum on 2012-12-16
Ubuntu 12.04

Hi,

When I press Check on the Update Manager, the following turns up.

```
W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Please help,

tehforum.

---

### Post by MoebusNet on 2012-12-16
> **tehforum said:**
> Ubuntu 12.04

Hi,

When I press Check on the Update Manager, the following turns up.

```
W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Please help,

tehforum.

From: [http://ubuntuforums.org/showthread.php?t=1966039](http://ubuntuforums.org/showthread.php?t=1966039)

I think it is the same issue again.

>  Have you thought that the getdeb repository might be down?

It is not an official repository owned by Canonical,so changing the server will not help.

Try disabling all the getdeb entries in Software Sources and see if the errors go away,then re-enabling them whenever the owners of the repository fix whatever problems the repository has.

It won't even load the getdeb.net home page. [http://www.getdeb.net/](http://www.getdeb.net/)

Good luck 

---

### Post by Cheesemill on 2012-12-16
The GetDeb site is down at the moment, you'll keep seeing these errors until they fix the site.

---

### Post by tehforum on 2012-12-16
Thanks for the replies guys.

Also, I've got a problem with Google Chrome, it's unresponsive, and is extremely prone to crashing with just one tab open all of a sudden.

What can I do?

I've tried restarting my computer, and that did not help.

Most of the time, I can't even scroll down, as the cursor icon is still in 'waiting' mode, then it crashes i.e "Page(s) unresponsive".

---

### Post by MoebusNet on 2012-12-16
Maybe this can help:

[http://ubuntuforums.org/showthread.php?t=1984514](http://ubuntuforums.org/showthread.php?t=1984514)

---

### Post by tehforum on 2012-12-16
Hmm,

also

usr/bin/jockey-gtk crashed

Internal error

FML.

jockey-gtk crashed with DBusExpection in call_blocking(): org.freedesktop.DBus.Error.ServiceUnknown: The name: 1.93 was not provided by any .service files

---

