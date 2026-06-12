---
title: "Ubuntu 7.10 Time Resets upon restart"
date: 2008-04-12
forum: General Help
---

### Post by lurker316 on 2008-04-12
I am dual booting with Vista Ultimate and Ubuntu 7.10.
The way I installed these OS is, first I installed Vista, then using the LiveCD I installed Ubuntu 7.10 Gutsy Gibbon onto another partition.

The time in Vista is the right time.
The time in the Bios is the right time.
The time in Ubuntu 7.10 is always off 4 or 5 hours.

I've manually reset it to the right time, upon reboot its messed up again.
I've set it to synchronize with the internet, but it seems to have no effect.

I dont know what could be causing this issue. Any help?

Asus P5e-VM HDMI
2x2Gb G.Skill DDR2 800
1x500Gb Western Digital HDD
1xGeforce 8800GT 512mb
E8400 Core2Duo CPU
1xLiteon DVDrw

Windows Vista Ultimate 64
Ubuntu 7.10 Gutsy Gibbon x86_64.

---

### Post by dcstar on 2008-04-12
> **lurker316 said:**
> I am dual booting with Vista Ultimate and Ubuntu 7.10.
The way I installed these OS is, first I installed Vista, then using the LiveCD I installed Ubuntu 7.10 Gutsy Gibbon onto another partition.

The time in Vista is the right time.
The time in the Bios is the right time.
The time in Ubuntu 7.10 is always off 4 or 5 hours.

I've manually reset it to the right time, upon reboot its messed up again.
I've set it to synchronize with the internet, but it seems to have no effect.

I dont know what could be causing this issue. Any help?


You do not have your system set up to the corect time zone, in a terminal:

```
sudo tzselect
```

---

### Post by lurker316 on 2008-04-12
> **dcstar said:**
> You do not have your system set up to the corect time zone, in a terminal:

```
sudo tzselect
```

It is setup correctly for America/Newyork.

But in anycase, I did it again using this command and upon Reboot, it resets to 4 hours behind the current time. I saved it also in the .profile and it still does it.

So now I ended up setting my timezone to Atlantic/Azores. And now both Local and UTC times are the same. I dont know whats the problem.

---

