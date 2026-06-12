---
title: "this is what i have done today"
date: 2006-10-04
forum: General Help
---

### Post by TheRingmaster on 2006-10-04
(I started off with kubuntu being the only os on my system.) first off I backed-up all of my important files. then I downloaded and burned gparted. I use gparted to create a partition for where my windows was gonna go (I NEED windows to play some games that I love). Then I installed windows to that partition.

Problems--

1) sound doesn't work in windows (this is not a problem as of right now)

2) when I start the computer now windows boots up. How can I make grub come up first so I can have a choice of what I want to boot into (also how do I even put windows into the grub menu?)

ps. As of right now I have Kubuntu 6.06.1

pps. If there are other post that are helpful please post them.

---

### Post by croak77 on 2006-10-04
Take a look at this wiki entry for recovering grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TheRingmaster on 2006-10-05
I use kubuntu. Does it matter if I use a Ubuntu disk?

---

### Post by TheRingmaster on 2006-10-05
> 4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub). 


I also need help finding this information.

---

### Post by Kateikyoushi on 2006-10-05
This will list your partitions.
```
sudo sfdisk -l
```

---

### Post by TheRingmaster on 2006-10-05
I can't seem to get to any download sites for super grub disk. Is there an alternative mirror that I could go to?

---

### Post by Patrick-Ruff on 2006-10-05
did you try the snaptic package manager?

---

### Post by TheRingmaster on 2006-10-05
> --------------------------------------------------------------------------------

did you try the snaptic package manager?

if you would have read my first post, you would know that I am in windows right now.

---

### Post by TheRingmaster on 2006-10-05
> **jpazindustries said:**
> I use kubuntu. Does it matter if I use a Ubuntu disk?
any answers to this question yet?

---

### Post by doobit on 2006-10-05
> **jpazindustries said:**
> any answers to this question yet?

Doesn't matter, as long as you can boot it and use the stuff that's on it. You are trying to get to the point where you can install GRUB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TheRingmaster on 2006-10-05
my /boot for kubuntu is at /dev/hda2

so what would I put into bash?


EDIT: I couldn't use gparted in some way to solve this problem, could I???

---

