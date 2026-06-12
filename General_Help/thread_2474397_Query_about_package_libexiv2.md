---
title: "Query about package libexiv2"
date: 2022-04-28
forum: General Help
---

### Post by andrew-q2 on 2022-04-28
Using Ubuntu 20.04.
I need version 0.27.5 of libexiv2 in order to build an app, but an "apt-get install exiv2" gives only 0.27.2
I understand little about package management and how these things progress.  I believe this version is available on some opensuse repository, but it would be nice if it was simply available via ubuntu/apt directly.
Who controls this sort of thing pls?  Does anyone know if it's work-in-progess to have the current version available within ubuntu?
Thanks

---

### Post by Holger_Gehrke on 2022-04-28
Once a version of Ubuntu is released, almost all packages in it stay at the released version for the lifecycle of the release. With very few exception (kernel, web-browsers) updates will only fix bugs, not upgrade a package to a new version.

That leaves you with two options:

[LIST=1]
[*]Compile libexiv2 yourself. You can then either install it in /usr/local/lib which is accessible system-wide and might break programs that need the older version or install it somewhere where ld.so doesn't look normally and give options to the configure script for your program to look there and possibly set LD_LIBRARY_PATH to include that directory when calling your program. 
[*]Update to Ubuntu 22.04 which does include the new version. 
[/LIST]

Holger

---

### Post by ActionParsnip on 2022-04-28
Possibly a PPA as well
[https://launchpad.net/ubuntu/+ppas?name_filter=libexiv2](https://launchpad.net/ubuntu/+ppas?name_filter=libexiv2)

Use at your own risk

---

### Post by andrew-q2 on 2022-04-29
Thanks folks, I'll see about going to 22.04.

---

### Post by DuckHook on 2022-04-29
I hesitate to muddy the waters for you, so take what follows with a large dose of salt:

When I want the stability of an older LTS (as I do on my servers, for instance), yet require the services of a newer app or library, then I will resort to running the newer app/library in either a VM or a container. That way, I get the best of both worlds. The VM/container has the added advantages of being effectively sandboxed for added security and can be rolled back to prior snapshots for added redundancy.

However, this strategy comes with some learning curves, so you need to decide beforehand if the advantages outweigh the time/effort cost.

---

### Post by andrew-q2 on 2022-04-29
Thanks @duckHook.  I'm no expert so as you hint, I don't think the learning curve for VMs etc. is worth it for me.
I'm wondering how much 22.04 has settled down by now.

---

### Post by DuckHook on 2022-04-29
> **andrew-q2 said:**
> …I'm wondering how much 22.04 has settled down by now.
It's important to remember that LTS stands for Long Term Support; not Long Term Stability.

22.04 is like any release, it is not that stable for the first few months. The usual rule of thumb is that it won't get truly stable until its first point release, which is scheduled for August sometime.

If yours is a production box, then waiting for the first point release is wise. If it is a tinkering box that you don't rely on, then nothing wrong with upgrading right away.

---

