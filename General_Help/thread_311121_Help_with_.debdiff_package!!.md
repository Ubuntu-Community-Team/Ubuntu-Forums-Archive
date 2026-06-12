---
title: "Help with .debdiff package!!"
date: 2006-12-02
forum: General Help
---

### Post by penguinmaster on 2006-12-02
I am trying to apply a debdiff package to fix the lockdown problem occuring in Synaptics.  I'm following this tutorial here:

[https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff)

I can get down to where you start ot apply the patch, but when I do that I get this output posted below.  Can anyone help me get past this point.  This bug in synaptics is bugging the hell out of me.  Either that can someone more experienced apply the patch and build me the normal .deb file??  Any form of help would be appreciated.

tom@lamp:~/a$ patch -p1<synaptic_0.57.11ubuntu13.debdiff
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Nru /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/aclocal.m4 /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/aclocal.m4
|--- /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/aclocal.m4        2006-10-11 18:17:35.000000000 +0200
|+++ /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/aclocal.m4        2006-10-23 16:17:01.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] 
Skipping patch.
1 out of 1 hunk ignored
can't find file to patch at input line 39
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Nru /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/configure /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/configure
|--- /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/configure 2006-10-11 18:17:38.000000000 +0200
|+++ /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/configure 2006-10-23 16:17:03.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] 
Skipping patch.
3 out of 3 hunks ignored
can't find file to patch at input line 122
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Nru /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/debian/changelog /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/debian/changelog
|--- /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/debian/changelog  2006-10-11 18:09:16.000000000 +0200
|+++ /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/debian/changelog  2006-10-23 16:14:23.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] 
Skipping patch.
1 out of 1 hunk ignored
can't find file to patch at input line 136
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Nru /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/gtk/rgmainwindow.cc /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/gtk/rgmainwindow.cc
|--- /tmp/MODE9Q3CBo/synaptic-0.57.11ubuntu12/gtk/rgmainwindow.cc       2006-10-10 14:25:58.000000000 +0200
|+++ /tmp/lBfDaiXzXF/synaptic-0.57.11ubuntu13/gtk/rgmainwindow.cc       2006-10-23 16:16:51.000000000 +0200
--------------------------
File to patch: 
Skip this patch? [y] 
Skipping patch.
2 out of 2 hunks ignored

---

### Post by lamego on 2006-12-02
Which lockdown problem are you referring to ?

---

### Post by penguinmaster on 2006-12-02
The link to the bug is here.  I'm trying to lock down firefox to v1.5, and it  refuses to lock it down.

[https://bugs.launchpad.net/distros/ubuntu/+source/synaptic/+bug/67146](https://bugs.launchpad.net/distros/ubuntu/+source/synaptic/+bug/67146)

If someone has another way around it I'd be happy to try that too.

---

