---
title: "dolphin wants root and won't launch"
date: 2017-05-19
forum: General Help
---

### Post by yonnie on 2017-05-19
running 16.10 and can't launch dolphin.  Just recently went from 16.04 to 16.10 and now the file manager won't work.  Tried to re-install dolphin, no change in problem.  Clicking on the launcher causes a login menu asking for root password off to the side of menu it says "kde-su".  Entering password just makes the box go away, fails to launch dolphin.
Got pcmanfm to work, dolphin still not.

---

### Post by TheFu on 2017-05-20
No idea.

If you run GUI programs with plain sudo, it is likely some config settings were created in your HOME with root:root as the owner.  
```
$ sudo chown -R thefu:thefu ~/
``` would correct this on my system with a few assumptions.

BTW, 16.10 support ends in 2 months.  17.04 is also a 9 month support release.  If you need longer support between swapping out the entire OS, 16.04 is the LTS.

---

### Post by yonnie on 2017-05-20
then why did it trick me into upgrading?  you think that command would cure the launch problem too?

---

### Post by TheFu on 2017-05-21
> **yonnie said:**
> then why did it trick me into upgrading?  you think that command would cure the launch problem too?

There are different settings which control whether you are reminded that a new release has happened.  I only run LTS releases. If you start with an LTS release, I don't think any non-LTS release reminders are shown. OTOH, if you start with a non-LTS release then all reminders are shown.  Is that being tricked over something so fundamental to the way releases under Ubuntu work?  I don't think so.  Did it automatically install without you clicking a button?  Nope.

We don't know exactly what the first issue is.  The command I provided makes lots of assumptions. You need to modify it for your situation.  It won't do any harm, if modified correctly, and it may correct an issue.  I wasn't there watching everything you did on the computer, so I don't know the issues which have been caused.  Using sudo too often is a common problem.  The only real fix for that is a better understanding of Unix file and directory permissions.  Things do work in a logical way, if that is understood.

---

### Post by yonnie on 2017-05-21
The version installed originally was 14.04 LTS, then updated to 16.04 LTS.  Just the other day I mistook the updater upgrade nag for an update and the next thing I knew I was getting 16.10.  Now I have Dolphin not working and unknown other issues with my primary office computer.

---

