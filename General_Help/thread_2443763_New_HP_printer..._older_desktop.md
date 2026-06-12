---
title: "New HP printer... older desktop"
date: 2020-05-19
forum: General Help
---

### Post by acefromspace on 2020-05-19
I'm using Ubuntu 16.04 on an older Dell inspiration desktop. Got a new printer (HP OfficeJet Pro 8028)
Was using an older HP printer with no issues (using HPLIP 3.16.3) Seems I now need HPLIP 3.19.5 for the new printer. Can I just get the newer version?
Also, thinking about doing a fresh install of Ubuntu 18.04 (but have till April 1021 before it's not supported) Would that help with the new printer install?
Right now, I think I can just connect the new printer (USB cable) and should be able to print. Eventually, will also want to scan. My son got a new HP printer awhile back and it prints fine (he's using Ubuntu 12.04 or 14.04) but he hasn't tried scanning.
One other issue... the older Dell desktop. Am I going to have issues with moving on to Ubuntu 18.04 (or even newer)? Have ran into issues before with older computers (like my laptop that didn't like Ubuntu 16.04)

---

### Post by CatKiller on 2020-05-19
> **acefromspace said:**
> Can I just get the newer version?

Maybe?

> Also, thinking about doing a fresh install of Ubuntu 18.04 (but have till April 1021 before it's not supported) Would that help with the new printer install?

Newer Ubuntu will come with newer everything, including CUPS and HPLIP. Whether that will actually help with your printer install, I have no idea.

> (he's using Ubuntu 12.04 or 14.04)

He should *definitely* upgrade - well, fresh install, really. Those releases have been unsupported for a long time now, meaning (at minimum) no security updates.

> One other issue... the older Dell desktop. Am I going to have issues with moving on to Ubuntu 18.04 (or even newer)?

Depends how old. If it's 32-bit then it'll upgrade to 18.04 (I think) but no further: 32-bit install images have been dropped. Sufficiently old Nvidia cards get dropped from their proprietary driver. Other than that, there's nothing major.

---

### Post by acefromspace on 2020-11-26
Update. Downloaded the new version ( hplip ) "auto installer" file. Installed it (thanks to  [https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index) )
It's been a long time since I've used Terminal... got so lazy because Ubuntu makes everything so easy. It was actually very easy... worked great!

---

