---
title: "Lubuntu  16.04   frequest crashes"
date: 2022-05-28
forum: General Help
---

### Post by manilaROOK on 2022-05-28
lubuntu frequest crashes

---

### Post by guiverc on 2022-05-28
I hope your system is offline.

Ubuntu 16.04 LTS reached it's end of *standard support* more than a year ago

> Ubuntu announced its 16.04 (Xenial Xerus) release almost 5 years ago, on  April 21, 2016. As with the earlier LTS releases, Ubuntu committed to  ongoing security and critical fixes for a period of 5 years. The  standard support period is now nearing its end and Ubuntu 16.04 LTS will  transition to Extended Security Maintenance (ESM) on Friday, April  30th, 2021.

- [URL="https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/"]https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/

[/URL]Lubuntu 16.04 LTS however reached it's support even longer ago, as being a *flavor* it came with only three years of support (If you read the [release announcement]("https://lubuntu.me/xenial-released/") you'll note it was *supported* by the team only until April 2019).  Whilst ESM support for 16.04 continues; this will **not **help Lubuntu system, and be aware many packages were only supported in ESM if replaced with the *snap* packages.

I'd suggest if your box is online, you'd use only *supported* systems, with the oldest *fully **supported *Lubuntu currently being Lubuntu 20.04 LTS. 

If your machine was *ppc* architecture; your release was the end of the road (*only ppc64el is supported beyond 16.04 which won't likely run on your hardware*)

If your machine was *i386* architecture; Lubuntu 18.04 LTS was the last *supported* (*though 18.10 & 19.04 did have support for i386 and Lubuntu, they reached EOL before 18.04 did/does as they weren't LTS releases*).

---

### Post by guiverc on 2022-05-29
Just an FYI.

If that was your bug report I just found, filing a bug report on an EOL system will just get closed; but next time please use ***apport*** tools so details from the system are included in the report.  ie.

`ubuntu-bug linux`

If filing a crash about the linux kernel itself which maybe appropriate for frequent crashes, though it'll depend on what is actually crashing... Clues of what crashed maybe found in /var/crash/ and yes it's often useful to seek help first; but there is no point on a release that has passed it's *End Of Life* as it'll just get closed* if noticed*.

The `ubiquity` (*if it was your report*) is what was used to install the system; meaning the "crash" occurred during installation itself. If it was the installer that crashed, support for that ended April-2019, so new filed bugs would need to be made on a supported system (ie. 20.04, 21.10 or 22.04) where `calamares` is now used as the installer. Lubuntu 16.04 also had an alternate ISO that used a different installer, but that isn't used anymore by *supported* Ubuntu systems.

For more details on filing bugs, please read [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

