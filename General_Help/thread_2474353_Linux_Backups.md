---
title: "Linux Backups"
date: 2022-04-27
forum: General Help
---

### Post by ray42 on 2022-04-27
Hello

I'm looking for an easy backup tool to backup everything, a clone so that I can reinstate in the event of a disaster.

I've seen a few Clonezilla, etc.

What is simple and does it without detailed knowledge.

Can I just "Create disk image", is that good enough? This looks simple enough.

System 76 suggests using GNOME Disks on their page:
[https://support.system76.com/articles/backup-files/](https://support.system76.com/articles/backup-files/)

---

### Post by DuckHook on 2022-04-27
> **ray42 said:**
> Hello

I'm looking for an easy backup tool to backup everything, a clone so that I can reinstate in the event of a disaster.

I've seen a few Clonezilla, etc.
Let's define terms:

[LIST=1]
[*]For proper *backup* you need something that makes incremental backups; not clones. Deja-Dup is already included with official flavours. Easy to use, installed by default, so why use something else? If this is a server or you are handy with the CLI, then rsync/rdiff are good too.
[*]If *cloning*, a number of strategies exist: Clonezilla is a reliable and trusted go&#8209;to. I've never used Gnome Disks but the linked instructions seem straightforward enough. Why not just try it? It will be easy enough to see if it works as advertised.
[/LIST]
There's a larger picture here that may be useful to you:

Backups are done for various reasons. Those end goals are what determine the best strategy, and you should examine those reasons first before deciding on a backup process.

**Example 1:**
If you want to protect your critical data from malware and ransomware attack, then cloning is not only overkill but counterproductive. After all, the last thing you want to do is to clone an infected system. Since modern malware bides its time and waits before encrypting your whole system, you won't know when you were infected. Therefore, cloning is inexact, unreliable and not the best solution.

The best method for malware recovery is to reinstall from scratch—thus ensuring that you have a pristine uninfected system—then recovering your data files from proper incremental backups. The incremental part allows you to go back to the versions of your data that you are sure are not corrupted.

**Example 2:**
If you want to protect your current system from, say, corruption caused by your own tinkering, or from a destabilizing upgrade, then cloning is attractive. But there are also alternatives like LVM/ZFS snapshots (super easy recoveries), or multibooting two or more separate installs on the same HDD to allow easy diagnosis and repair.

I do both snapshots and multiboot and find this combo a much better strategy than cloning. To be honest, I've found cloning to be a poor strategy overall. When something goes wrong, I want to start over with the assurance of a pristine environment. Cloning tends to drag in all of the instabilities that may have caused the problem in the first place. And if the problem is malware related, then a cloned image simply cannot be trusted, so the problem isn't solved.
> What is simple and does it without detailed knowledge.
Your desire can't be satisfied. Backing up is about preserving your most precious data. This cannot be done without addressing details. While the process of backing up is not especially difficult, it does require a commitment from the user to put in the time and effort to understand security fundamentals and execute on processes.

In the case of proper backups, you must commit to a schedule of rotating media. In the case of LVM snapshots/multiboots, this requires a learning curve and ongoing maintenance. Even cloning is not just fire&#8209;and&#8209;forget. You need to keep track of which clone in a series is the latest, test whether it restores properly (before you are under the gun and find out at that critical juncture that it doesn't work), and then clone properly and restore properly. These are not trivial exercises.

There ain't no such thing as a free lunch. But it isn't especially complicated either so it shouldn't cause the sort of dismay that so many people approach it with. For a good primer on backing up, see the link in my sig.

---

### Post by HermanAB on 2022-04-27
In general, it is not recommended  to backup the whole system, since Linux is easy to install from scratch - much faster than restoring a full clone.  Also, one day when the inevitable happens, you may want the latest Linux and not an old tired version. So rather just backup your data and be done with it.

---

### Post by ray42 on 2022-05-08
Yes, hmm. Thought provoking and all relevant.

:)

---

### Post by TheFu on 2022-05-08
Perhaps working backwards will help to select what needs to be backed up and how?
[Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) is my restore process.  It is split into 3 parts roughly along the time it takes to do each step, which is about 15 minutes each. ¹/&#8323;, ¹/&#8323;, and ¹/&#8323;.   <--- I was looking for an excuse to try some vim super/subscripts. ;)

In less than 45 min of restore efforts, we have a fresh install with all the critical programs, settings, data and files ready to go.  It is "our system" again.  Sound interesting?

---

