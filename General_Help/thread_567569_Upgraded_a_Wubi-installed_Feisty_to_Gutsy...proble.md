---
title: "Upgraded a Wubi-installed Feisty to Gutsy...problems"
date: 2007-10-04
forum: General Help
---

### Post by neodorian on 2007-10-04
I should begin by stating that I expect things to go wrong and I'm just playing around anyway so I'm out nothing but time here.  Anyway, I have a tablet PC that has no optical drive.  I have used Wubi to install Feisty in the past but since the Gutsy beta has been running so well on my desktop, I figured I would try this out.  I installed Feisty on the tablet with Wubi, did all updates, rebooted, ran:

```
sudo update-manager -d
```

and let it spend the night downloading and installing the upgrade.

Now I just finally finished and rebooted.  When I boot into Ubuntu now, it sits on the splash screen for a while loading, then kicks me out to a command line.  The top of the screen says 

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu6) Built-in shell (ash)
```

and my prompt is "(initramfs)"

Like I said, this was kind of a half-assed way to get Gutsy on there so I'm not surprised it didn't work, still is there anything I could have done otherwise or can do to fix it?  Otherwise I'll just wait for the real Gutsy Wubi to come out.

---

### Post by ago on 2007-10-05
You are better off waiting for the new version. In fact if you have already used Ubuntu via wubi and you like it, I'd encourage you to go for a full installation of Gutsy once it's released.

---

### Post by neodorian on 2007-10-05
Well, like I said, there is no optical drive in the tablet and it won't boot to just any CD drive (stupid Toshiba).  I guess I can always use your tool to move it to its own partition.

---

### Post by Gan on 2007-10-16
> **ago said:**
> You are better off waiting for the new version. In fact if you have already used Ubuntu via wubi and you like it, I'd encourage you to go for a full installation of Gutsy once it's released.
So if I am using Feisty with wubi, am perfectly fine with it and not planning to move it to a real partition, then I better off not upgrading it to Gutsy... right?

---

### Post by darkcrab on 2007-10-19
> **ago said:**
> You are better off waiting for the new version. In fact if you have already used Ubuntu via wubi and you like it, I'd encourage you to go for a full installation of Gutsy once it's released.

I have a question, I installed Wubi on my laptop because I cant install linux on a seperate partition on my laptop. i have no plans to upgrade from feisty, and It has been working great for me. It thought the whole reason wubi was created was to make installation of linux easier for people? Are you saying that its not ok to run linux this way? Im confused?:confused:

---

### Post by ago on 2007-10-19
> **neodorian said:**
> Well, like I said, there is no optical drive in the tablet and it won't boot to just any CD drive (stupid Toshiba).  I guess I can always use your tool to move it to its own partition.

You can use Unetbootin

---

### Post by ago on 2007-10-19
> **darkcrab said:**
> I Are you saying that its not ok to run linux this way? Im confused?:confused:

Wubi is more vulnerable to hard reboots than a normal installation (and there is no suspend/hibernation) plus there is a slight degradation of performance (which is affected by ntfs fragmentation). Hence it's perfect to use for a few days and weeks until you make up your mind (far better than a LiveCD or a VM), but if you like what you see and find yourself using Ubuntu on a daily basis and move sensitive data to it, I would try to move to a dedicated partition for the long term. LVPM should make the transition quite easy.

---

