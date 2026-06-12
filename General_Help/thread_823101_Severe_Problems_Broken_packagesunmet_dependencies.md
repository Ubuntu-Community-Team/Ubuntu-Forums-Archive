---
title: "Severe Problems: Broken packages/unmet dependencies"
date: 2008-06-08
forum: General Help
---

### Post by LeeU on 2008-06-08
All of a sudden I'm having all kinds of problems. I am running Heron 8.04. When the system is started and the desktop is displayed, I get an error message saying "couldn't open x-nautilus-desktop:///", and it flashes several times. Then, when I try to do updates, it tells me that my "installed packages have unmet dependencies", and give me the following errors:
> 
E: /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-18-generic_2.6.24-18.26_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/firmware/2.6.24-18-generic/ipw2100-1.3-i.fw')
E: /var/cache/apt/archives/linux-headers-2.6.24-18_2.6.24-18.32_all.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/nautilus-data_1%3a2.22.3-0ubuntu2_all.deb: subprocess new post-removal script returned error exit status 139
E: /var/cache/apt/archives/rhythmbox_0.11.5-0ubuntu6_i386.deb: subprocess new pre-removal script returned error exit status 139
E: /var/cache/apt/archives/seahorse_2.22.1-0ubuntu2_i386.deb: subprocess new post-removal script returned error exit status 139


When I open the Package Manager, it says that I have broken packages. I run the filter, tell it to fix the packages, and get the same errors as above.

When I try to go back into the Package Manage, I now get the following errors:

> 
E: Problem parsing dependency Depends
E: Error occurred while processing bind9-host (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


I also have problems with Firefox 2 crashing, and I can't open Nautilus. It just begins to open and then crashes.

Any ideas what is happening? I'm really having some problems here.

---

### Post by LeeU on 2008-06-09
Does anybody have any kind of a clue, or should I just dump this verion and go back to Gutsy? (From personal experience and what I have read across the Internet, this was a Windows-type mistake, released far too early.)

---

