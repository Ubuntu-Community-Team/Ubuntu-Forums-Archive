---
title: "RAM vs. Swap"
date: 2007-03-30
forum: General Help
---

### Post by emid on 2007-03-30
I have 2 GB of ram in my desktop and it seems as though it never gets fully utilized.  Most of the time I'm probably not maxing it out, but I notice that my swap usage will often be at 700-800 MB even though my ram usage will only be at 50% (1GB out of 2GB).  Is the data in the swap negatively affecting performance? If so, is there a way to utilize more of the system ram to negate this?  It seems I hardly use much more than a little over a gigabyte.

---

### Post by hikaricore on 2007-03-30
I've never owned that much ram so I can't help much, but with that much you might want to adjust your "swappiness"

Here's a few links with info:

[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html)
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed) (middle of page)
[http://www.ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://www.ubuntuforums.org/showpost.php?p=1255511&postcount=43)
[http://www.serbuntu.net/ubuntu/tips/swappiness](http://www.serbuntu.net/ubuntu/tips/swappiness)

Swappiness does have some downfalls if some rogue application decides to use a **** ton of memory processes may die, but with 2 gigs of memory, I doubt you'll ever have that problem.

---

### Post by theslut on 2007-03-30
are you using a kernel that supports memory over 1gB?

---

### Post by emid on 2007-03-30
Thanks hikaricore, that seemed to do the trick.  My system does seem more responsive now.  I often run XP in vmware and it does seem much snappier than before.  I'll see how many things I can run at once before it starts to bog down so I can get a better estimation of the results.


> **theslut said:**
> are you using a kernel that supports memory over 1gB?

I have no idea.  I think I'm running the standard kernel.  I'm on an AMD 64 machine.

---

