---
title: "Syncing a folder to a different partition"
date: 2015-09-16
forum: General Help
---

### Post by Shkat on 2015-09-16
Hello everyone, got a simple question here.

I want to sync a folder from my desktop to another partition I've got, but the thing is i cant seem to find any way to do so. I do not want symbolic or hard links, just that the folder at the desktop gets synced to another partition in case the main one blows up.
Does anyone know a way to do it?

---

### Post by papibe on 2015-09-16
Hi Shkat

Take a look at Unison. Here's a [tutorial]("https://help.ubuntu.com/community/Unison").

Let us know how that goes.
Regards.

---

### Post by Shkat on 2015-09-16
Thanks for that! Probably what I need, gonna give it a look as soon as I'm home. Thanks!

---

### Post by v3.xx on 2015-09-16
The program "rsync" is part of the default install.  Its a terminal only syncing program that a GUI front end can be added.  There are different front ends to choose from, like Unison. I use "grsync"; a simple interface.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by Habitual on 2015-09-18
[http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

---

