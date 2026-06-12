---
title: "critical temp 54c xubuntu 7.04"
date: 2007-11-24
forum: General Help
---

### Post by bwinfrey on 2007-11-24
There are a lot of similar posts out there, but this one is a little different.

 I upgraded from 6.06 to 7.04 on 11/21 and had to reinstall apmd, acpi, acpid, cdr, laptop-mode, libapm, power-*, xfburn (ie. xubuntu-desktop) so the upgrade mechanism could perform the upgrade.

Everything was working fine yesterday (11/23/07) I was using eclipse all morning, but now my computer shuts down when the system load hits 100% while eclipse is loading.

So, what changed you ask...

This morning I made some changes (DOH!).   You see it's a low powered system, so I try to eliminate what I don't need.

Well, I first disabled services that looked unnecessary, or weren't used in previous dist. 
- acpmd, acpid, powernowd, mdadm, mdadm-raid, nfs-kernel-servers, tftpd-hpa  
I then  added the remaining components for the hplip printing service, and added a printer. When I tried to print a document the system froze.  I had to reboot several times to get back into X the system was hanging before GDM loaded.  I finally got booted in recovery mode and disabled GDM so I could see what was going on.  The system was shutting down due to the critical temp message at 54 degrees.  Obviously I screwed something up, but I can't remember the initial settings in services.

I have a different system (desktop) that this one was cloned from.  I set the services startup the same, but still the same issue.

I have tried every combination of powernowd, apmd and acpid to no avail.  As soon as I start eclipse the system shuts down with the same message.

I added powernow-k8 to modules as I saw in another post, reinstalled all the power related items from the previous list, rebooted and viola it works.  The problem is I don't know what happened in the first place.

I was able to run eclipse, synaptic, service settings, and relaunch GDM all at the same time.  Again I rebooted and GDM came up no problem, I was able to log in and eclipse started.  I then opened a term and compiled some code and there was no problem.

I'm not sure what broke the system and I'm not sure what fixed it, but I would like to know if anyone has insight.

Please don't post "me too stories" just relevant answers as to what the cause of the problem is.

Thank you,
bwinfrey

---

