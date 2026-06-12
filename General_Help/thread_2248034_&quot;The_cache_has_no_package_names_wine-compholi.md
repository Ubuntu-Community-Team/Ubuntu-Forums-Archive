---
title: "&quot;The cache has no package names wine-compholio-i386&quot; error."
date: 2014-10-11
forum: General Help
---

### Post by 0310aditya on 2014-10-11
Hey guys so lately i have been having a few problems,

On my desktop there is a red minus sign and when i click on it it says "The cache has no package names wine-compholio-i386"  and so on. I do not know the cause and i would like it to be fixed all help appreciated.  Next, i don't know if this is related but recently i tried installing tor browser using the instructions online on how to install it by adding the sources etc. This happened to no avail and it wont find the package so that is a seperate issue. My main concern is that every time i run the sudo-apt-get update command these are the results:

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<trusty>/main/binary-amd64/Packages  404  Not Found [IP: 93.95.227.222 80]


W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<trusty>/main/binary-i386/Packages  404  Not Found [IP: 93.95.227.222 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.

Help with this also will be appriciated thanks!

---

### Post by deadflowr on 2014-10-11
The two things are unrelated.
The wine-compholio message is a known issue
See here
[https://bugs.launchpad.net/pipelight/+bug/1318321](https://bugs.launchpad.net/pipelight/+bug/1318321)

You might want to remove/disable the torproject entries, then run an update.
That should at least clear the message, and then try adding the torproject entries again.
(Or at least change the entries the second time.)
I would suggest posting the source.list so others can see what the entry says...

---

### Post by 0310aditya on 2014-10-12
Hey thanks for your reply! I took your advice and opened the sources.list file in gedit and deleted all the torproject entries and than ran a sudo apt-get update. No more errors. And as for the wine-compholio issue i installed wine-compholio:i386 (as it said on the launchpad link you have me) instead of the AMD64 version that i originally had no more minus sign! I guess this thread is solved thanks for your help!

Jeremy

---

### Post by xmbwd on 2014-10-24
You might want to wait before marking this one solved; I've had the same problem and applied the linked solution (Post #2: "**sudo apt-get install wine-compholio:i386**") several times.  The error keeps coming back. . . .  sometimes after a week.  Sometimes after a month.  I assume it is when there is another wine update.  

But it definitely is not a permanent solution -- at least for me.

---

