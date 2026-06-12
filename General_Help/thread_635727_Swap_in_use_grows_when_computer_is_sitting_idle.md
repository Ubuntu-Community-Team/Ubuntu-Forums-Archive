---
title: "Swap in use grows when computer is sitting idle"
date: 2007-12-09
forum: General Help
---

### Post by gila_monster on 2007-12-09
Hi, gang.

I'm currently running Xubuntu Gutsy on my Gateway laptop. All in all, things work all right. But I have noticed lately (in the past week) that the swap space in use increases as time goes by, even if the machine is basically sitting idle. (Idle = Thunderbird running, no other user apps.) As the swap is used up, the machine becomes slow to switch contexts.

Just today, the machine has gone from almost no swap used to over 800M. 200M of that was in the past six hours with nothing running.

Is there something in a recent update that changes how the swap is used? Is there a known issue with Thunderbird here? I tried searching on "swap" and related terms, and didn't really see anything.

Thanks.

---

### Post by yabbadabbadont on 2007-12-09
If it only happens while Thunderbird is running, even if you aren't actively using it, then it probably indicates a memory leak in Thunderbird.  Try rebooting and then letting it sit without Thunderbird running and see if it still happens.  If so, then the leak is somewhere else.

---

### Post by gila_monster on 2007-12-15
For what it's worth, I found the culprit. Wasn't Thunderbird, but a background process. Would take it about a day to chew up the swap. I removed it, and all is well.

Thanks for the response.

---

### Post by TreeFinger on 2007-12-15
What was the process?

BTW how do you view running processes from terminal?

---

### Post by yabbadabbadont on 2007-12-15
> **TreeFinger said:**
> BTW how do you view running processes from terminal?

```
ps ax
```
Or
```
top
```

Better yet, install htop and use it.

---

