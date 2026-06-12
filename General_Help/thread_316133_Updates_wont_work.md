---
title: "Updates wont work"
date: 2006-12-10
forum: General Help
---

### Post by voodoonirvana on 2006-12-10
I can't seem to do any updates. When I click the update icon it tells me:
[B]
Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.[/B]

When I try to do it through the terminal I get this:
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache
[/B]

I reinstalled Firefox yesterday so that may have something to do with it but Im not quite sure.

---

### Post by Malakia on 2006-12-10
Have you tried running dpkg --configure -a to see if that fixes the problem. If your updating and it doesn't get finished because the computer gets turned off or you log it, it will cause these types of problems.

---

### Post by voodoonirvana on 2006-12-10
> **Malakia said:**
> Have you tried running dpkg --configure -a to see if that fixes the problem. If your updating and it doesn't get finished because the computer gets turned off or you log it, it will cause these types of problems.

Okay so I did that. Now it is showing me the update icon, but it is shaded over and says that I already have a package manager running. :confused:

---

### Post by taurus on 2006-12-10
Paste the output of this command here!  Maybe you have something running in the backgraound...

```
ps -A
```

---

