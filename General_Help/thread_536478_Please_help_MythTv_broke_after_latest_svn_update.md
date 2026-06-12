---
title: "Please help MythTv broke after latest svn update"
date: 2007-08-27
forum: General Help
---

### Post by sjitan on 2007-08-27
I'm getting an error saying that my version of libmyth is older than the one compiled so it recommended that I do a distclean.
I do a distclean and still doesn't work. This is affecting both my backend and frontend, any ideas what I'm doing wrong? 
Follow up:
I deleted the ld.so.cache and I also moved all libmyth libraries that it was linked too and did a make distclean then make
and here's what I get on the frontend wheni run it

mythfrontend: Symbol `_ZTV15LineEditSetting' has different size in shared object, consider re-linking
2007-08-27 16:01:54.742 This app was compiled against libmyth version: 0.20.20070717-1
but the library is version: 0.21.20070820-1
You probably want to recompile everything, and do a
'make distclean' first.
2007-08-27 16:01:54.744 Failed to init MythContext, exiting.
mythtv@htpc1:~$ 

thank You
P.S. Running Feisty Fawn

---

### Post by superm1 on 2007-08-28
Sounds to me like you are mixing source and packaged versions.  Bad idea.  Go one way or the other, not a mix of the two.  Do note, 0.20.2 has been packaged and is in feisty-proposed.  looking at that version though you had some variation of 0.21 it would appear. Choose one or the other !:)

---

### Post by sjitan on 2007-08-28
That does makes sense but I don't know how I did that.

All I did was an svn update and recompiled and this started happening.
I've deleted all instances of the old mythtv and removed all packages and still get the same error.
I've re-downloaded from svn and still to no avail.
Any help would be much appreciated.

---

### Post by superm1 on 2007-08-28
> **sjitan said:**
> That does makes sense but I don't know how I did that.

All I did was an svn update and recompiled and this started happening.
I've deleted all instances of the old mythtv and removed all packages and still get the same error.
I've re-downloaded from svn and still to no avail.
Any help would be much appreciated.

Check in /usr/local/bin/myth*, /usr/bin/myth* /usr/lib/libmyth* /usr/local/lib/libmyth*.

Odds are you missed a file or two.

---

### Post by sjitan on 2007-08-28
Will try that tonight and post back, thank you so much for your help.

Regards,

---

