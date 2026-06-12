---
title: "Offline package installation problems"
date: 2013-02-21
forum: General Help
---

### Post by Griffnoids on 2013-02-21
Hello. I apologise if this has been answered elsewhere, I've seen probably 10 different threads all telling me different things.

I'm trying to get a _fully offline _installation of about 8 packages to run on Ubuntu 12.04. This machine never has and never will be online, so it just has a default 12.04 install with no updates.  

I've downloaded the packages (which came with about 200 other deb files which I assume are dependancies) from a seperate machine using **apt-get --download-only**

I then copied these 200+ deb files to the **/var/cache/apt/archives** folder on the offline machine.  I was under the impression that if I then ran **apt-get install XXXXXX** and there was no net connection it would still do a lookup to the package location but it doesn't and I receive several errors including "**Package XXX is not available, but is referred to by another package**" and then a list of errors all saying "**E: Unable to locate package XXXX**", "**E: Unable to locate package YYYYY**" etc.

If I need to download further packages in order to get these to properly install then I will, but I haven't found any solid solutions yet and am looking for the simplest solution possible.

Many thanks in advance to anyone who can assist :)

---

