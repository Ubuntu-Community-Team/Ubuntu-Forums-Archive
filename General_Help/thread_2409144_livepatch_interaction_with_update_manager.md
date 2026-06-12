---
title: "livepatch interaction with update manager"
date: 2018-12-28
forum: General Help
---

### Post by kmand on 2018-12-28
I run update-manager frequently and I'm trying to understand the interaction with livepatch. For example for the last week or so update manager flagged a kernel security patch

Installed version: 4.15.0.42.44 Available version: 4.15.0.43.45

Which marks 12 packages for update. A day after these appeared livepatch went from unpatched to

patchState: applied version: "46.3" with 17 CVE's listed. I presume this handled the security issues that are in the security patches that update-manager keeps listing.

What I still don't understand is the interaction with update-manger. Do I just have to keep filtering out kernel patches manually, and does livepatch do anything about patches that normally require a reboot but are not in the kernel?

---

### Post by TheFu on 2018-12-29
You've probably seen this: [https://wiki.ubuntu.com/Kernel/Livepatch](https://wiki.ubuntu.com/Kernel/Livepatch)

> 
The Livepatch Service intends to address high and critical severity Linux kernel security vulnerabilities, as identified by Ubuntu Security Notices and the CVE tracker. Since there are limitations to the kernel livepatch technology, some Linux kernel code paths cannot be safely patched while running. There may be occasions when the traditional kernel upgrade and reboot might still be necessary. 

---

### Post by kmand on 2018-12-30
This only makes it more confusing. How does one know when a kernel patch that is not covered by livepatch is necessary? So it appears that I not only need to keep manually filtering  out kernel patches that update-manager is presenting, but never know if some of them are actually ones that livepatch is not handling.

---

### Post by TheFu on 2018-12-30
Any kernel patch that isn't *address high and critical severity Linux kernel security vulnerabilities* isn't usually important to anyone using livepatch services.  Stability and uptime is the primary goal, not patching for every possible kernel issue.

If you want all kernel patches, then livepatch isn't a suitable solution alone.

I don't use livepatch. If we need HA, then we setup active/active clustering and take 1 of those systems down.  If the scalability requires more systems, then we'd use containers and Kubernetes to run rolling upgrades for the containers over time.  Of course, container management is totally different from normal VM or OS management, so any comparison is weak.

We have scheduled downtime every week to perform patching of physical or VM systems.  Every once in a while, perhaps once every other year, an issue will be so important that we will patch outside the normal, approved, window. We do that only on high risk systems that are known to have the problem and are being exploited in the wild.  Most of our systems aren't internet facing so patching can wait.

I don't have a good answer for your questions. The link is all there is, unless you have a Canonical support contract. Then you can call them.  I assume this isn't a server in a house basement.

BTW, nobody here works for Canonical.

---

