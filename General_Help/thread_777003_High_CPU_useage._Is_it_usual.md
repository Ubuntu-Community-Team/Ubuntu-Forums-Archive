---
title: "High CPU useage. Is it usual?"
date: 2008-05-01
forum: General Help
---

### Post by Robbyx on 2008-05-01
This is not just in FF. I have applied the bug fix to FF re i/o excesses.

I have a dual intel cpu. Smithfield.

The process showing cpu is only gnome-system-monitor. CPU1 shows 98% CPU2 22-60%.

I had the same problem under gutsy. Now it is happening under HH.

Is this unavoidable?

Robin

---

### Post by charonn0 on 2008-05-01
I believe this is a [known issue with Gnome System Monitor](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847) itself, where it eats up a lot of CPU cycles whenever you open it. No real solution as yet, except to use a different program to view running processes. I like htop, even though it doesn't have a GUI. You can get it from the repos.

---

### Post by Robbyx on 2008-05-01
> **charonn0 said:**
> I believe this is a [known issue with Gnome System Monitor](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847) itself, where it eats up a lot of CPU cycles whenever you open it. No real solution as yet, except to use a different program to view running processes. I like htop, even though it doesn't have a GUI. You can get it from the repos.

I have installed htop. It is also showing high but not as high CPU useage. I wonder if there is a way of reducing it?

Robin

---

### Post by hyperair on 2008-05-01
Check what programs are using your CPU. Htop can arrange your processes by CPU usage.

---

