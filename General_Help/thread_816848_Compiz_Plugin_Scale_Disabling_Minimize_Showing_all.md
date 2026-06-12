---
title: "Compiz Plugin Scale Disabling Minimize Showing all Windows including Minimized"
date: 2008-06-03
forum: General Help
---

### Post by chemuduguntar on 2008-06-03
Hi,

Is there a way to get the scale plugin to show windows that are currently minimized as well, or as a work around disable minimizing windows through another plugin?

I would like to be able to view all open windows, but minimizing them does not show them ...

---

### Post by Forlong on 2008-06-03
> **chemuduguntar said:**
> Is there a way to get the scale plugin to show windows that are currently minimized as well
No, that's currently not possible, because of a limitation in the X server.
> **chemuduguntar said:**
> or as a work around disable minimizing windows through another plugin?
What do mean by that? You know *you* are responsible for minimizing windows, right? :)
> **chemuduguntar said:**
> I would like to be able to view all open windows, but minimizing them does not show them ...
I rarely ever minimize windows. Four viewports + Expo + Scale is more than enough for me.

---

### Post by zergamat on 2009-05-15
what i did, and it works great:

- download file showall.py 
from this thread 
[http://ubuntuforums.org/showthread.php?t=481038&page=2](http://ubuntuforums.org/showthread.php?t=481038&page=2)
and make it executable (file from ryanhaigh)
- in compiz settings/commands make a link to the showall.py and in edge bindings give the same edge that scale effect use (you can use both on the same edge)

it works v.fast

---

### Post by flomar on 2010-04-21
Finally filed a bugreport, see [[feature request] mapping of minimized windows]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/566896")

---

