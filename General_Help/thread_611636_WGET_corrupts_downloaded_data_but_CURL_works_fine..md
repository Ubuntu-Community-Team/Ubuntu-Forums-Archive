---
title: "WGET corrupts downloaded data but CURL works fine. No Updates possible with APT-Get"
date: 2007-11-13
forum: General Help
---

### Post by BenderIII on 2007-11-13
Hi,

one problem occurs on my Ubuntu 7.04 installation.

WGET corrupts most of the larger downloaded archives. GZ or Bzip2 giving me CRC-Error messages. :shock:

As a result of this behaviour it's not possible to update/upgrade my Ubuntu installation to the 7.10 version. Am I thinking wrong that the apt-get also uses wget to download the deb-files???

To correct this problem I tried to purge the wget, ark, bzip2 and reinstalled them. But this didn't help.

When trying to manually download the archives with CURL everything works perfect. No CRC-Errors.

Any suggestions how to fix this download errors?

---

### Post by BenderIII on 2007-11-20
Yeah,

I managed to install a fresh new 7.10 gutsy from DVD and all was fine.
But just for one day (or less) :(

Now I have the same problem as described.
apt-get cant install larger deb-packages as they are corrupted. 
trying to WGET them into to cache dir shows the same failures while using CURL is working.

I did not know exactly what package I installed last before this behaviour re-occured. 

What can I do to fix this????? All suggestions really appreciated.
Or a hint for what packages/libs are related to the download process within apt-get/aptitude.

I hope I won't need to install again a fresh server :(

---

