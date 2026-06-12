---
title: "Posting and confirming bugs"
date: 2006-08-06
forum: General Help
---

### Post by Rinnan on 2006-08-06
I just bought a new laptop: an Acer Aspire 5601AWLMi.  A lot does work on Dapper on this machine, but two vital parts do not, sleep (suspend or hibernate) and audio.

I would like to post bugs on launchpad but really don't know how.  Can someone help me through this?

Here are my questions:

How do I know what packages to file the bug under?  I know that audio is related to ALSA, but the bug could presumably be in alsa-drivers, alsa-libs, the kernel, or even some other part of the OS.  The sleep problem has the same situation -- I know it's acpi something, but what?

I need to be more specific about my hardware I suppose.  Should I just submit the output of lspci with my reports?

After trying some other distros, I'm coming to think it's an upstream problem (can't seem to get it to work in any distro).  Do I need to determine that for sure, or do the Ubuntu developers do it?  If they do determine that it's an upstream problem, do they file bug reports upstream, or do I?

It would be nice to get these as confirmed bug reports and not unconfirmed bug reports.  Is there someone else who has these same problems with the same laptop?

I've noticed that other bug reports are extremely specific, pointing out exactly where in the OS the failure is, and even include patches to fix it.  I'm afraid that my reports won't be that specific, because I haven't (yet) been able to pinpoint where the bug is.  Should I report the bugs, knowing so little, or try to work through them first, so I can (possibly) give a more specific bug report?

---

### Post by asimon on 2006-08-08
> **Rinnan said:**
> How do I know what packages to file the bug under?  I know that audio is related to ALSA, but the bug could presumably be in alsa-drivers, alsa-libs, the kernel, or even some other part of the OS.  The sleep problem has the same situation -- I know it's acpi something, but what?
If you are unsure on which package to file a bug, just file it against the package "Ubuntu".

> **Rinnan said:**
> 
I need to be more specific about my hardware I suppose.  Should I just submit the output of lspci with my reports?
This is definitely a good idea for hardware related issues. (use 'lspci -vv')

> **Rinnan said:**
> 
After trying some other distros, I'm coming to think it's an upstream problem (can't seem to get it to work in any distro).  Do I need to determine that for sure, or do the Ubuntu developers do it?  If they do determine that it's an upstream problem, do they file bug reports upstream, or do I?
No, you don't need to determine that for sure. If it's an upstream bug it will be filed upstream. But if you are sure it's and upstream issue then it won't hurt if you file the bug upstream yourself. ;-)

> **Rinnan said:**
> 
I've noticed that other bug reports are extremely specific, pointing out exactly where in the OS the failure is, and even include patches to fix it.  I'm afraid that my reports won't be that specific, because I haven't (yet) been able to pinpoint where the bug is.  Should I report the bugs, knowing so little, or try to work through them first, so I can (possibly) give a more specific bug report?
Well, just post what information you have. If a developer tries to fix this bug and need more information he will ask for it and tell you what to do to provide that information.

Here a pointer for bug reporting: [ReportingBugs](https://wiki.ubuntu.com/ReportingBugs).

---

