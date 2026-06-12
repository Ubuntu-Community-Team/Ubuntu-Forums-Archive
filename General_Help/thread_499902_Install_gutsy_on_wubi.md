---
title: "Install gutsy on wubi"
date: 2007-07-13
forum: General Help
---

### Post by ilidza on 2007-07-13
How I can install gutsy on wubi? Thanks

---

### Post by ago on 2007-07-13
The lupin initrd would need to be compiled on a gutsy machine. 

I may release one, but we are merging with ubuntu so to have a proper one will be a few more weeks.

---

### Post by mschraier on 2007-09-22
I am inquiring as to what the status of the Gutsy inclusion is at.  I used Wubi for Fiesty and it works great.  Have had no issues whatsoever.  The upgrades with regards to screen resolution that are to be included in Gutsy is what I am waiting for.  I do not know how to adjust screren resolution otherwise.  Please advise as to the status and if u have a solution for screen resolution with fiesty.

---

### Post by ago on 2007-09-22
You can use the binary at [http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/)

It's an early release, mostly intended for developers. The items 

0 Use CD
1 Read Only

Should work
For the rest your luck may vary.
But it would be good to start having some testing anyway. If you go beyond 1 Read Only, back up your data. Always use the latest daily build, redownload even if yours is 1 day old

---

### Post by BernardB on 2007-09-27
Tried to install gutsy using a binary at that web address, it failed.
It hangs at 8% while scanning disks with the partition editor (why does it need this? I love Wubi because I don't need to repartition if I don't want to).
Using a standard Dell Inspiron 1501; any suggestions?

---

### Post by ago on 2007-09-27
> **BernardB said:**
> Tried to install gutsy using a binary at that web address, it failed.
It hangs at 8% while scanning disks with the partition editor (why does it need this? I love Wubi because I don't need to repartition if I don't want to).
Using a standard Dell Inspiron 1501; any suggestions?

Because the partitioner does a lot of things other than changing the partition table, like creating and formatting (virtual) disks, checking free space...

That's a known bug, not fixed yet, only read-only install is available now

---

### Post by Rellin on 2007-09-27
hmm I guess I'm ubuntu-less until the official gutsy comes out.  for some reason feisty doesn't work on my laptop.

EDIT: actually I have an idea.  since the part of feisty that is incompatible with my laptop is xorg is it possible for me to upgrade my wubi Feisty install via command line and then it will magically start working?

---

### Post by Rellin on 2007-09-28
bump for my edit.

---

### Post by BernardB on 2007-09-28
It may but it certainly didn't work for me (HAL broke; see my post history).

Irrespective, please update this thread when the aforementioned bug is fixed and I'll give Wubi for Gutsy another attempt.

---

### Post by ago on 2007-10-01
You can install the required video drivers without upgrading hal (see apt docs on how to skeep updates for a particular package)

---

### Post by BernardB on 2007-10-06
Just downloaded the latest gutsy installer; it doesn't seem to be able to download the ISO.
Is it offline or is the installer's URL mistaken?

---

### Post by ago on 2007-10-06
Do you mean wubi 7.04? Hmm that should work, but you can always download the 7.04 alternate ISO manually and place it in the same folder where you have wubi.exe

---

### Post by BernardB on 2007-10-06
> **ago said:**
> Do you mean wubi 7.04? Hmm that should work, but you can always download the 7.04 alternate ISO manually and place it in the same folder where you have wubi.exe
No, by "gutsy installer" I mean the lastest 7.10 alpha's at [http://wubi-installer.org/devel/minefields/](http://wubi-installer.org/devel/minefields/).

Perhaps it is the same "Trying again in 5 seconds"-bug as [this]("http://ubuntuforums.org/showpost.php?p=3486299&postcount=36").

---

### Post by ago on 2007-10-06
There is a new build up, rev 314

---

### Post by BernardB on 2007-10-06
Tried it; the ISO now downloads correctly.

On first boot, the screen turned black after starting Ubiquity but before showing the wallpaper.
On second boot, the screen showed the wallpaper and mouse for a second before turning black again.
On third boot, using safe graphics mode, it does seem to correctly start Ubiquity and X but refuses to install due to some other installation being present; I assume this was created from the first attempt above.

Hence, I told Windows to remove Ubuntu but save the ISO, then redownloaded the installer to be sure and told it to reinstall Ubuntu.
However, it does not use the saved gutsy-desktop-amd64.iso (aren't codecs working better on i368 regardless? - Love the simple screen but perhaps an "Advanced"-button would be handy) but starts downloading a new ISO.
Will move the ISO around and edit this post later.

Edit:
Did that, booted with safe graphics mode, now it hangs at 5% while partitioning (while creating the ext3 / partition on Loopback).
Would I also have such paritioning problems using the alternate ISO's installer?

---

### Post by ago on 2007-10-07
> **BernardB said:**
> 

Edit:
Did that, booted with safe graphics mode, now it hangs at 5% while partitioning (while creating the ext3 / partition on Loopback).
Would I also have such paritioning problems using the alternate ISO's installer?

No that's a bug in wubi, I'll fix that probably today.

---

### Post by musicalmike on 2007-10-10
Will it be possible to use wubi to install gutsy when gutsy is released fully?

---

### Post by ago on 2007-10-11
[http://ubuntuforums.org/showthread.php?t=572147](http://ubuntuforums.org/showthread.php?t=572147)

---

