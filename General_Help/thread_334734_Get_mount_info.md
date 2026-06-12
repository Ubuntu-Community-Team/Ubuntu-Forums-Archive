---
title: "Get mount info?"
date: 2007-01-09
forum: General Help
---

### Post by earobinson on 2007-01-09
Ok two simple questions.

One how to I check how many times a partition has been mounted since it was last checked (eg if its on its 3rd mount till it checks)

Second how do I get the settings for mounting eg it will check every 30 days and 7 times.

Edit: Also is there any way to push the file system checking to shutdown? Or sync it across computers so they all check at the same time

---

### Post by Jussi Kukkonen on 2007-01-09
> **earobinson said:**
> Ok two simple questions.

One how to I check how many times a partition has been mounted since it was last checked (eg if its on its 3rd mount till it checks)

sudo  tune2fs -l <devicename> | grep "Mount count"

you can also change things with the same program.

---

### Post by earobinson on 2007-01-09
thanks!

Also is there any way to push the file system checking to shutdown? Or sync it across computers so they all check at the same time? I know I could write a script but was looking for something that was already created

---

