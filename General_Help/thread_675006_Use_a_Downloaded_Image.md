---
title: "Use a Downloaded Image"
date: 2008-01-22
forum: General Help
---

### Post by Hoom@n on 2008-01-22
Hi!
I don't want to download Edubuntu again, so i put Wubi-7.04.04.exe to the same place that hardy-desktop-i386.iso was; But again the wubi wants to download Edubuntu. What can I do to install Edubuntu from my image?
Thank you.

---

### Post by ago on 2008-01-22
hardy is ubuntu 8.04 you will have to wait for wubi-8.04 for that which should be out soon (but it will require a newer iso anyway)

If you use wubi-7.04 you need the ubuntu-7.04 ALTERNATE ISO.

---

### Post by Hoom@n on 2008-01-22
Thank you, but I mean can I hack wubi in some way? I mean there shouldn't be so much difference in installing 7th and 8th version, so by changing the wubi's isolist it may install the 8th version. Is that possible?

---

### Post by ago on 2008-01-22
Nope. For 8.04 you will have to wait a bit, but it's a matter of days now.

---

### Post by Hoom@n on 2008-01-22
Thank you. But just by the way my problem is that I don't have a cd/dvd rom. Is there ann program to boot my computer with a file on my disk? (I mean boot with the Ubuntu iso)

---

### Post by ago on 2008-01-22
Yes you can use netinstall techniques (will do a full installation). Or use wubi in read-only mode (will boot the ISO as is without CD, in a read-only environment).
For the first one there are guides on the web.

---

### Post by candtalan on 2008-01-22
I am an existing k/ubuntu user, and help newcomers locally. I am just trying Wubi because it seems like a really good idea. I also run a machine as a seed for (mostly ubuntu related) a few selected torrents.

When I saw that the install process was mostly a long download of ubuntu 7.04 alternate, - it started at less than 20 kb/sec and after a few hours went up to 60 kb/sec, a couple of questions came to mind:

1) Is there a way I can contribute to the wubi up/download traffic by seeding to a specific torrent tracker? I would be very glad to help although it would only be in a small way.

2) Quite a few long time windows users that I see are not on broadband, and might want to obtain a ubuntu alternate CD - could this be used by some means instead of the normal wubi install download?
tia

---

### Post by candtalan on 2008-01-23
> **candtalan said:**
> 
2) Quite a few long time windows users that I see are not on broadband, and might want to obtain a ubuntu alternate CD - could this be used by some means instead of the normal wubi install download?
tia

Ah! I see a CD image can be used:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Hoom@n on 2008-01-26
> **ago said:**
> Yes you can use netinstall techniques (will do a full installation). Or use wubi in read-only mode (will boot the ISO as is without CD, in a read-only environment).
For the first one there are guides on the web.

Thank you, but how can I do the second?

---

### Post by ago on 2008-01-26
> **candtalan said:**
> 
1) Is there a way I can contribute to the wubi up/download traffic by seeding to a specific torrent tracker? I would be very glad to help although it would only be in a small way.
We (mostly hampus to tell the truth) are working on a new downloader (see [www.launchpad.net/snappy](www.launchpad.net/snappy)) That will support segmented downloads and will be considerably faster than the current one. But it's unlikely we will be able to add bittorrent support in the first release.

> 2) Quite a few long time windows users that I see are not on broadband, and might want to obtain a ubuntu alternate CD - could this be used by some means instead of the normal wubi install download?
tia
Wubi 7.10+ can use the Live ISO and/or physical Live CD

---

### Post by Hoom@n on 2008-01-28
Thanks alot for all the helps. I installed it with CD! (my cd-rom started working again!)
Thank you again.

---

