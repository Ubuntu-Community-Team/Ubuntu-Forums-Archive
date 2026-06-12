---
title: "How to uninstall apache2 (built from source)"
date: 2007-05-20
forum: General Help
---

### Post by loathsome on 2007-05-20
Hi there,

I successfully compiled apache2 from source. Now I want to uninstall it, but how? There's no "uninstall" option in the makefile.

Thanks!

---

### Post by BitTorrentBuddha on 2007-05-20
I believe the only way to uninstall compiled files that come without a 'make uninstall' option is to manually go through and delete all that was installed. You could try installing and uninstalling apache2 with apt and see if it overwrites the compiled files before removing via the package manager.

---

### Post by loathsome on 2007-05-21
Thanks for your reply.

Is there any easy way to find all the files I made when I compiled? No, the deb-package did not overwrite, it installed to another location. Thanks.

---

### Post by loathsome on 2007-05-21
Man, no way I'm going to look up, search and investigate EVERY SINGLE FILE just to delete apace2. There's **got to** exist another way of doing this.

---

### Post by DoctorMO on 2007-05-21
All make files should come with a make remove or make uninstall or make destroy are you sure there isn't one?

as for the files, you can get a list of the files in the install log and use that in a script... that is if it generated a log file. (this is why we use debs ;-))

---

### Post by loathsome on 2007-05-21
Yes, I'm positive there's no "remove / uninstall" option. I tried to create a package using checkinstall first, but it failed (as always)

Anyway, apache2 is spread all over everywhere now :P I need a freaking way to remove this.

Thanks for your reply!

---

### Post by zvacet on 2007-05-21
```
whereis file_name
```

This will tell you where apache is.If there is no other way to uninstall it you have to go to every folder/directory with apache2 files and delete it manualy.

---

### Post by loathsome on 2007-05-21
> **zvacet said:**
> ```
whereis file_name
```

This will tell you where apache is.If there is no other way to uninstall it you have to go to every folder/directory with apache2 files and delete it manualy.

Thanks a lot ;) If I for example do this: ```
loathsome@frozenpenguin:~$ whereis cowbell
cowbell: /usr/bin/cowbell /usr/lib/cowbell /usr/X11R6/bin/cowbell /usr/bin/X11/cowbell /usr/share/man/man1/cowbell.1.gz
```

Is that every single cowbell-file?

---

