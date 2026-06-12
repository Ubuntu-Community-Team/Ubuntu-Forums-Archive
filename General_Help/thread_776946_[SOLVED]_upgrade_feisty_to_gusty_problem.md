---
title: "[SOLVED] upgrade feisty to gusty problem"
date: 2008-05-01
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-05-01
OK, so I tried to upgrade a testbox today that I hadn't used for a while. It still runs Feisty (7.04) and I wanted it to upgrade to Gusty (7.10) and eventually to Hardy (8.04).
I started Adept, installed the latest updates which worked just fine, then tried the Dist Upgrade which starts fine as well. But then, at one point a Error Message come up saying that it can't fetch some upgrades and list all the Main, Universe, etc links. So, I'm really stuck here, is there no way to upgrade from Feisty to Gusty anymore, since Hardy is out?
Fresh install is not an option at the moment since the CD drive doesn't work, so I rely on the internet to upgrade.

Any ideas what I can do, which download server to choose? I tried different ones, just in case. But no idea what else I can do.

Cheers,
Steve

---

### Post by cckrobinson on 2008-08-09
Did you ever figure this out?|  I too have a Kubuntu box that is sitting on Feisty and I'd like to upgrade to Hardy.  When I attempt the upgrade through Adept Manager it tells met that Hardy is available but then it fails right away because I'm not allowed to go from Feisty to Hardy.

How can I go to Gusty first?

---

### Post by cckrobinson on 2008-08-09
I was able to successfully upgrade from feisty to gusty by following this thread (post #2).

[http://ubuntuforums.org/showthread.php?t=837063](http://ubuntuforums.org/showthread.php?t=837063)

---

### Post by cdtech on 2008-08-09
I did mine by changing everything in my sources.list to gutsy:
```
deb http://archive.ubuntu.com/ubuntu/ gutsy universe main
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe main
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
```
Did a "sudo apt-get update" and then did "sudo apt-get dist-upgrade"

Works great....

---

### Post by Linux&amp;Gsus on 2008-08-10
Uh, ya, forgot about that thread... :oops:
I figured it out. But don't remember the exact detail anymore.

Anyways, after a few days of research it worked. As far as I remember there was some sort of setting not correct and it also seemed to that the servers hadn't been too responsive. Might have just been my imagination but it seemed to me that the upgrade from 7.10 to 8.04 was faster than 7.04 to 7.10.
But I really don't remember all the details anymore.

I had also some sort of trouble while upgrading to Hardy. At one point the upgrade froze at a time where it shouldn't have. I let it sit there for about 3 or 4 hours. Then I just decided to reboot.
If it works, great. If not, it's really "only" a testbox for Linux, so no real value lost. At the end of the day I know that there is an issue with the video card. The screen looks like an way overexposed image. No way to adjust that.

Unfortunately I had some emergencies on my desk and I actually changed desks, as well. So, I didn't really have much time to play around with it. But soon-ish I thought about getting maybe something like "No Machine" running on there so I don't rely on the machines graphics card.
I did had it on there but since the upgrade it's not working any more. I need to spend some time with that machine to make it fully functioning again.


One thing I must say though.
It's an about 5 year old 1.6GHz AMD Duron with 512MB RAM and a known broken 32MB ATI video card and runs Hardy just fine. Not exactly a racing machine of course but it runs up-to-date Linux with a full blown KDE.
Kudos too all who make something like this possible. A Vista install CD would probably explode when seeing such a machine. :lol:
I might have had some troubles. But at the moment I really can't of troubles that would make me run away from Linux. Just the fact that I still can use such an old and broken system is mind blowing.

Cheers.

---

