---
title: "Compiz settings reset after each reboot"
date: 2008-04-28
forum: General Help
---

### Post by alxhastngs on 2008-04-28
Every time I reboot my visual settings are defaulting back to "None".  This in turn disabled my title bars and multiple workspaces, as well as all my compiz settings. 

Using hardy 8.04 and nVida 8400M.  These features work perfectly fine after I change them, its just after every reboot, I have to change the settings back.  

Any help with this?

---

### Post by alxhastngs on 2008-04-30
bump.  Still having this problem.

---

### Post by Zorael on 2008-05-01
Do the settings reset in ccsm, as well? (package name **compizconfig-settings-manager**)

---

### Post by alxhastngs on 2008-05-01
Yep.  My Visual settings are reset back to Basic, and all my ccsm settings go back to default.

---

### Post by Zorael on 2008-05-01
Have you tried changing backend to flat-file, under Preferences?

---

### Post by alxhastngs on 2008-05-01
Yeah just tried it, no difference.

---

### Post by TheSamurai on 2008-05-01
type the following into terminal

```
compiz --replace
```

i think this is the right one. after that is done, leave the terminal open and restart. this should fix the problem. it's been awhile since i've played around with it. sorry if this is incorrect. hope it helps.

---

### Post by bobbarnes1981 on 2008-07-04
I have the same problem and that solved it. Thanks.

---

### Post by TheSamurai on 2008-07-04
cool. glad it helped.

---

