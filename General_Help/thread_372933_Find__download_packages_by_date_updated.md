---
title: "Find / download packages by date updated?"
date: 2007-02-28
forum: General Help
---

### Post by Mr. Picklesworth on 2007-02-28
I am hoping to get updates for my computer via another computer, without having to download the latest CD image. This would involve using the online package repositories and downloading the necessary packages with a different computer, then putting them on removable storage to transport them.
Is it possible to search for and download packages in Main that have been updated since a particular point in time?

---

### Post by firefly2442 on 2007-02-28
This might be a little too complicated but if both computers are on the same network, you could make the computer connected to the internet act as the repository for the other.  Or maybe just install a proxy on the machine so that the one without Internet access can get on the Net.  You can also check /var/cache/apt/archives/

This is where it stores packages until you clear the cache.  If both computers are running the same CPU architecture (i386, AMD64, etc.) you could just copy those over and then figure out some way of retrieving the apt-get update listing for the computer with the Net connection.

Not exactly ideal solutions but maybe someone else has a better idea.:neutral:

---

