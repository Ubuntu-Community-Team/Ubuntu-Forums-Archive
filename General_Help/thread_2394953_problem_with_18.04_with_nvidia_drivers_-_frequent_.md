---
title: "problem with 18.04 with nvidia drivers - frequent Xorg crash - advice"
date: 2018-06-24
forum: General Help
---

### Post by fr4nko on 2018-06-24
Hi all,

I would like to have some advice from ubuntu's community. Since I switched to 18.04 on my desktop PC, several months ago, I am experiencing very frequent Xorg crash after suspend. What happens is that all the applications are closed and I am logged out. When I log in again the "send report" windows open up and it points out to a xorg crashes and it seems related to nvidia drivers but I am not sure.

Just for information, about my graphics card, here an excerpt of lspi:

> 01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2)

and I have otherwise a standard installation.


At the beginning I thought that such a big problem was going to be fixed more sooner than later but actually it is still there and I am tired of that.

I am considering:
- downgrade to a previous ubuntu release
- install another distro
- report the bug and try to get it fixed

I would like to have some advice. Is someone experiencing a similar problem with 18.04 ? What could be a safer solution ? is 18.04 too unstable in general ?

---

### Post by #&amp;thj^% on 2018-06-24
When you say "switched to 18.04 " is this a upgrade or clean fresh install?
And how did you install the nvidia driver?
These questions will be helpful for us to help you.:)
I'm now using
```
NVIDIA GF114 [GeForce GTX 560 Ti] driver: nvidia v: 390.67
```
With no issues.

---

### Post by fr4nko on 2018-06-24
Hi,

as for 18.04 I didn't do a fresh install but I have made an upgrade from the previous ubuntu version.

The driver have been installed using the standard application "Software & Updates" then "Additional Drivers". I have currently:

Using NVIDIA driver metapackage from nvidia-driver-390 (propietary, tested)

the other options that appears are nvidia proprietary 340 and nouveau but I didn't try them.

Do you think that a fresh install could help ? I thought not since I have a pretty standard install and I didn't tweak the system in any way.

---

### Post by #&amp;thj^% on 2018-06-24
> **fr4nko said:**
> Hi,

as for 18.04 I didn't do a fresh install but I have made an upgrade from the previous ubuntu version.


This is what I first thought.

> **fr4nko said:**
> 

Do you think that a fresh install could help ? **_[U]I thought not since I have a pretty standard install and I didn't tweak the system in any way_[/U]**.
It wouldn't hurt (If you are willing to do this.)>>>This release introduced a Lot of new changes IE: like coming from 16.04 to 18.04, but if upgraded from 17.10 to 18.04 would have been a little more of a smoother ride. :)
From 16.04 to 18.04 could have left a lot cruft behind, Now I'm not saying this can not be repaired nor am i saying we can get you to a pristine state again, but this will require a lot of time and effort on both you and the members here trying to help you.

---

### Post by fr4nko on 2018-06-24
Ok, thank you, I will try a fresh install when I have time. I hope it will helps :-)

---

### Post by fr4nko on 2018-07-02
Hi all,

I have made a fresh install of my ubuntu 18.04 and for the moment I am running with the nouveau driver for the nvidia card.

I love how everything is snappy and works smoothly with the nouveau driver but I cannot run steams games so I am afraid I have to switch back to the proprietary nvidia driver. In addition I am wondering if the system will begin to crash again xorg like with the previous install.

I am wondering if there is something (reasonable) that can be done to use nvidia driver only for games. I don't want to dual boot because it is too time consuming and annoying.

Any suggestion or idea ?

---

### Post by Autodave on 2018-07-02
I would go ahead and install the correct Nvidia driver now. Get it either from the repositories or go to Settings -> Additional Drivers. Or, Settings -> Software & Updates -> Additional drivers.

Your issue was *probably *due to upgrading rather than doing a clean install. Personally, I learned a while ago that updating doesn't work often enough to even consider.

---

### Post by SeijiSensei on 2018-07-03
I have an NVIDIA GTX 750 (not a Ti) running in 18.04 with the 390 driver.  It currently stands at 390.48 and works without a hitch.  I usually install the driver from the command prompt with "sudo apt install nvidia-current".

During the period when 18.04 was in beta, the NVIDIA driver installation seemed a bit wonky.  Those problems appear resolved in the final release version.

---

### Post by #&amp;thj^% on 2018-07-03
> **SeijiSensei said:**
> I have an NVIDIA GTX 750 (not a Ti) running in 18.04 with the 390 driver.  It currently stands at 390.48 and works without a hitch.  I usually install the driver from the command prompt with "sudo apt install nvidia-current".

During the period when 18.04 was in beta, the NVIDIA driver installation seemed a bit wonky.  Those problems appear resolved in the final release version.

+1 ;)
And I have used the driver from:
```
apt policy nvidia-390
nvidia-390:
  Installed: 390.67-0ubuntu0~gpu18.04.1
  Candidate: 390.67-0ubuntu0~gpu18.04.1
  Version table:
 *** 390.67-0ubuntu0~gpu18.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status

```
With no issues>> I also agree with  SeijiSensei while in development the nvidia driver's from both the PPA and Ubuntu Repos had a bit of a rough patch but smooth sailing here for me even with a higher version kernel.
```
 uname -a
Linux me-750-417c 4.17.4-041704-lowlatency #201807031235 SMP PREEMPT Tue Jul 3 12:39:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```
**I do not recommend though that you stray from the kernel that ships with Bionic.**

---

### Post by sourcejedi on 2018-07-20
> **fr4nko said:**
> Hi all,  I would like to have some advice from ubuntu's community. Since I switched to 18.04 on my desktop PC, several months ago, I am experiencing very frequent Xorg crash after suspend. What happens is that all the applications are closed and I am logged out. When I log in again the "send report" windows open up and it points out to a xorg crashes and it seems related to nvidia drivers but I am not sure.  and I have otherwise a standard installation.  At the beginning I thought that such a big problem was going to be fixed more sooner than later but actually it is still there and I am tired of that.  I am considering: - downgrade to a previous ubuntu release - install another distro - report the bug and try to get it fixed  I would like to have some advice. Is someone experiencing a similar problem with 18.04 ? What could be a safer solution ? is 18.04 too unstable in general ?   "Critical upstream bugfix missing in Ubuntu 18.04 - frequent Xorg crash after suspend"  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1776887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1776887)    There's a workaround that can be used if you edit the boot options.  I'm really hoping Ubuntu get the upstream patch applied in a few weeks now.

---

