---
title: "Another frustrating DVD playback issue"
date: 2007-01-27
forum: General Help
---

### Post by beercz on 2007-01-27
Fellow ubuntu users, please help.

I have searched high and low throughout these forums to no avail, so I am creating a new thread on this subject.

My problem is that if I attempt to play a DVD as a user other than myself I am unable to open the DVD.

This seems to happen in Totem, gxine, mplayer and vlc

If I am logged in myself I can play the DVD without problems.  I have all the necessary packages and codecs installed (otherwise I would not be able to play the DVD at all).

So, this seems to me to be a permissions problem, but I can't find it.

Can anyone shed light on this?

I am running Dapper.

Thanks in advance.

---

### Post by sizzlor on 2007-01-27
what is the output of this command?
```
sudo ls -al /media
```

this may also be an issue whereby the 'other user' needs to belong to the same user groups as you to be able to access the DVD drive..

---

### Post by sizzlor on 2007-01-27
you might want the compare the output of the command ```
groups
``` while logged in as yourself and the other user.

---

### Post by beercz on 2007-01-28
> **sizzlor said:**
> what is the output of this command?
```
sudo ls -al /media
```

this may also be an issue whereby the 'other user' needs to belong to the same user groups as you to be able to access the DVD drive..

> root@danpc:~# ls -al /media
total 12
drwxr-xr-x  3 root root 4096 2007-01-28 01:54 .
drwxr-xr-x 21 root root 4096 2006-09-23 11:22 ..
lrwxrwxrwx  1 root root   13 2007-01-28 01:54 cdrom -> /media/cdrom0
drwxr-xr-x  2 root root 4096 2007-01-28 01:48 cdrom0

Looking tha the groups issue now.

Thanks for the responses sizzlor.

---

### Post by beercz on 2007-01-28
Solved!! :-)

Definately a groups issue.

Added the user to the same groups as my own.

Overlooked the groups command.

Thanks again sizzlor.

I really should stop doing things like this at 3am!!

---

### Post by sizzlor on 2007-01-28
hehehe, no prob -- glad to help.

---

