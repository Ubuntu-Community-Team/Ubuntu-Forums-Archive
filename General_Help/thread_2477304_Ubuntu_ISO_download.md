---
title: "Ubuntu ISO download"
date: 2022-07-20
forum: General Help
---

### Post by vbgf3 on 2022-07-20
Hi,

Is the Ubuntu ISO download updated ? I mean, is the ISO updated every few weeks ? Or is it the same ISO file since the version's release date ?

---

### Post by oldfred on 2022-07-20
Very rarely is the ISO updated. It has to have a major glitch.
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

But each point release, .1, .2. etc is a new ISO including all the updates since previous release.

[https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906](https://discourse.ubuntu.com/t/jammy-jellyfish-release-schedule/23906)
And if you want stability you stay with the XX.04 or XX.04.1. Installs with any point after .1 get rolling release to next point & all its updates.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
But your 22.04 or 22.04.1 will say it is  22.04.2 when it is released but stay with original kernel. And now some programs are updated. 
If you use snaps, they have their own updates.

---

### Post by guiverc on 2022-07-21
You didn't provide any ISO details.

Ubuntu releases do use the *year.month* format, thus Ubuntu 20.04 LTS is the 2020-April release of the product. That detail does **not** change in subsequent re-releases of the product, they just have a .1/.2 etc added with new ISOs spun as oldfred already said; ie. Ubuntu 22.04.1 LTS or the updated ISO for Ubuntu 22.04 LTS (2022-April release) still has the same name, with no reflection of the expected to be released 4th-August-2022(*note: schedules exist for releases so dates are known, but even without looking at the schedule the releases are regular & like clockwork** except for rare delays by a week or two*).


Maybe what has you confused is pre-released ISOs (ie. *alpha* or *beta *ISOs) eg. I downloaded earlier a *daily* of the *jammy* product that will be released as Lubuntu 22.04.1 LTS for *Quality Assurance* or QA-testing; that *daily *has a date of 20220720  (2022-July-20) which is actually found in the metadata & data within the ISO, as the ISO is just called [jammy-desktop-amd64.iso]("http://cdimage.ubuntu.com/lubuntu/jammy/daily-live/20220720/jammy-desktop-amd64.iso") with the name only changing if it's declared the release product.  That *daily* date can still be found in the final product too if you look.  Also note *daily* implies once per day, but it's probably best to think of it as *interval*.  There are parts of the cycle where the *daily* can be  spun weekly, and days where it's spun many times, the second *daily* of the same date will have a .1 added; third *daily *on the same day would say .2 etc.

Some ISOs close to release are classed *FINAL *or *RC* (*release candidate*), terms though I personally just ignore as I still just grab (`zsync` *so I'm downloading only differences*) the latest *daily* ISO (*same thing*) and record my QA testing on the *daily* page, the web sites where I record my results knows the 20220720 ISO I'm about to start testing is an *alpha**/beta/final/RC* and will record is as such*.  *The *daily* I'm about to test has all upgrades applied already up to when it was built.

*Daily* ISOs are intended for QA (*Quality Assurance*) testing purposes, and not production systems, however, if you need say a Ubuntu 20.04 LTS using the 5.15 kernel stack, as that ISO hasn't been released yet, I'd consider using the *daily* of it myself for my systems.

---

### Post by grahammechanical on 2022-07-21
When we install Ubuntu we get the option to update the system as part of the installation process. If we tick that option we will get an up to date Ubuntu. Of course, once we start using Ubuntu we can run Software Updater regularly and keep Ubuntu up to date.

There really is no need to go to the time and expense of producing new ISO images every few days or weeks. New ISO images have to be produced not only for Ubuntu but for all the official flavors built upon Ubuntu.

Regards


Regards

---

### Post by SeijiSensei on 2022-07-21
There is a "daily live" build of Ubuntu 22.04 at [https://cdimage.ubuntu.com/jammy/daily-live/current/](https://cdimage.ubuntu.com/jammy/daily-live/current/). For the adventurous, there's a daily build of 22.10 at [https://cdimage.ubuntu.com/ubuntu/daily-live/current/](https://cdimage.ubuntu.com/ubuntu/daily-live/current/).

---

