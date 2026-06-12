---
title: "Strange issues with remote login and local account"
date: 2008-03-06
forum: General Help
---

### Post by dcymbal on 2008-03-06
I am seeing this problem on 2 different boxes, one running Ubuntu 7.10, the other Kubuntu 7.10.

Both these boxes are setup for NIS with automount.  Users running WinXP use cygwin to XDMCP to these systems to get remote X access to their desktops.  That works fine.

Problem I am seeing is that there is 1 local account for these boxes 'bubba'.  If I cygwin/XDMCP to either of these boxes and login as bubba, I get the desktop but after a few menu clicks the X session seems to get extremely slow to the point of being unusable.  This is only if logged in as 'bubba' remotely,  If from the same XP system I XDMCP to the same linux box and login with a NIS account I can use the session all day without issue.

If I login as 'bubba' from the console to either system that works fine as well.  So:

1) Local account login from console - OK
2) NIS account login remote via XDMCP - OK
3) Local account login remote via XDMCP - NO GOOD

Any ideas of explanations of this?  I believe this was working fine on the kubuntu box at least when it had 7.04.  We don't use the 'bubba' account all the time so I am not sure if this was the case with the ubuntu box.

---

