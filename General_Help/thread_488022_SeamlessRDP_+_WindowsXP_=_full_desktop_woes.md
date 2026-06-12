---
title: "SeamlessRDP + WindowsXP = full desktop woes?"
date: 2007-06-29
forum: General Help
---

### Post by octoberdan on 2007-06-29
On the windows xp box, I unpacked the seamlessrdp archive into c:\seamlessrdp, logged out of windows xp, and then on the ubuntu box tried:
```

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad" 10.26.1.31

```
logged in only to discover that an entire desktop session was running. What the heck is going on? I've varrified everything is in the right place... Any and all help is appreciated greatly. Thank you for atleast reading this far.

---

### Post by njwiley on 2007-07-04
Make sure that Fast User Switching and the Welcome Screen are turned on.  Control Panel|User Accounts|"Change the way users log on or off".  Haven't figured out a way to make this unnecessary and it bugs me.

---

### Post by www.rzr.online.fr on 2008-03-06
Have you tried seamless on a virtual machine also ?

--
[http://rzr.online.fr/q/RDP](http://rzr.online.fr/q/RDP)

---

