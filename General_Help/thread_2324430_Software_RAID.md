---
title: "Software RAID"
date: 2016-05-13
forum: General Help
---

### Post by anon24 on 2016-05-13
So, I want to know how to put two of my internal SSDs in RAID. I did have them in fake RAID, but had issues.

---

### Post by lukeiamyourfather on 2016-05-13
When installing Ubuntu the software RAID can be setup during the drive partitioning section of the installer. What RAID level are you considering? You might also considering ZFS instead of Linux software RAID.

---

### Post by anon24 on 2016-05-13
I have no clue... I don't particularly want my OS drive to be RAID with my other two SSDs. I just want my two other drives to be read as one drive. I already have Ubuntu 16.04 set up the way I want, I don't really want to go through the install process again.

---

### Post by Geoffrey_Arndt on 2016-05-13
Not really much of a benefit to have software RAID on ssd's . . how hard is it to click/mount the devices? . . takes 2 seconds and using dual-windows, easy to manage the directories & files.

After reading your other posts, I suggest you tread carefully so you don't hose your system yet again.

---

### Post by DuckHook on 2016-05-14
People automatically jump to RAID too often. It's complex and a maintenance headache. Most of all, it's overkill for what most ordinary users are trying to achieve. Consider LVM instead. Much easier than RAID sans the complexity. Doesn't require a reinstall or other messing around. Read up about it first. Make sure you are comfortable with it and it does what you want. The following might be informative:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by anon24 on 2016-05-14
> **Geoffrey_Arndt said:**
> Not really much of a benefit to have software RAID on ssd's . . how hard is it to click/mount the devices? . . takes 2 seconds and using dual-windows, easy to manage the directories & files.

After reading your other posts, I suggest you tread carefully so you don't hose your system yet again.

*First* off, the benefit of being able to fit more on the partition is more than enough of a reason for me to want the two drives to be read as one. Just because you don't find something useful, doesn't mean other people won't see the utility.

*Secondly*, what benefit is there in having to mount an SSD? Why not just have it mount by default at startup? I get not mounting a SATA drive because having the drive running all of the time decreases its life significantly, but that is not really the case with an SSD. At least not to the extent of a SATA drive. 

*Thirdly*, really? Are you just trying to be contrary because someone wants things a certain way on their system that you find to be silly? Maybe that's two seconds of my life that I don't really want to waste mounting a hard drive. I'm not mad or anything, but mind your own if all you have to offer is a critique of my time management / preferences for how I like things set up.

*Lastly*, my system didn't crash because of RAID, it crashed because someone suggested that I try Bumblebee and Bumblebee caused my system to go haywire. Before my attempt at installing Bumblebee, my system was working fine. Yes, I had an issue _after that_ reinstalling Ubuntu and it just happened that taking my drives out of RAID fixed that issue. I had installed Ubuntu twice before that with no issues and had the same RAID setup. 

I might add that I have three SSDs in my laptop and I didn't intend on including the one that Ubuntu is installed on in the RAID setup, just the two other SSDs. So, why would I have to reinstall to make that happen / how would that "hose my system" when the operating system wouldn't even be on those drives? I would agree if I had been suggesting that I was going to include the drive that the OS is on in the RAID, but alas, I didn't. I happen to have an internal SATA drive as well and all of the same data is still on it, completely intact, from my very first installation of Ubuntu.

---

### Post by anon24 on 2016-05-14
> **DuckHook said:**
> People automatically jump to RAID too often. It's complex and a maintenance headache. Most of all, it's overkill for what most ordinary users are trying to achieve. Consider LVM instead. Much easier than RAID sans the complexity. Doesn't require a reinstall or other messing around. Read up about it first. Make sure you are comfortable with it and it does what you want. The following might be informative:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

Thank you for being helpful! I will give this a try. It looks like it could be a good way to go.

---

### Post by Geoffrey_Arndt on 2016-05-14
The views expressed are a growing trend - - and it's OK for you to have a different opinion and practice.   JIC (just in case) you're not aware, in Ubuntu, mounting drives, partitions, remote network storage, can all be done automagically if one knows how (read up about "etcee" /etc & fstab).   But, in my personal use-case, I find a one-second mount via mouse click to be a non-issue.   I have no daemons, agents or cron jobs that require automatic access to that file set other than Dropbox (& Cloud is another reason for decline in RAID usage).

---

