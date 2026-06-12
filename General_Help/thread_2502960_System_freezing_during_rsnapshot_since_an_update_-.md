---
title: "System freezing during rsnapshot since an update -  WQ_UNBOUND"
date: 2024-12-08
forum: General Help
---

### Post by Freek07 on 2024-12-08
Hi all,

I have a backup machine running rsnapshot.
It was been working great for a couple of years, but ever since an update a couple of weeks ago, it's been freezing for the whole time the rsnapshot is linking files (2 hours) - I can't even SSH onto it, virtual machines are crashing,...
Backups (i.e. the filed being linked) are on separate hard disks; system drive is not utilized at that time. Also, the cpu load is low (single-digits) - still, the system just doesn't respond to anything.

Looking into it, there's this curious message in the logs: 

workqueue: inode_switch_wbs_work_fn hogged CPU for >10000us 1024 times, consider switching to WQ_UNBOUND

Is there a workaround?
I'm running LTS (noble), kernel 6.8.0-49-generic.

6.8.0-49-generic #49-Ubuntu SMP PREEMPT_DYNAMIC

I was messages about this being fixed in 6.5.x, but apparently it returned in 6.8? Can I fix it?

Thanks!

---

