---
title: "Random crash on Ubuntu 16.04"
date: 2017-05-29
forum: General Help
---

### Post by scpsc on 2017-05-29
Hi everyone!

I recently purchased a DELL Precision T7810 on which I installed Ubuntu 16.04.

lsb_release -a shows:
```
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
```

And the hardware is:
2 Intel Xeon E5-2620
256G SSD M.2
+ 2T HD
32G RAM
AMD FirePro W4100

My only problem is a "random" crash that occurs quite frequently (twice this morning but some days there is none). And I can't figure out what's wrong exactly, as it doesn't seem to be linked to a specific usage. Here is what I get in syslog and kern.log at the time of those crashes:

```
May 29 13:04:28 precision7810 kernel: [ 3974.676457] DMAR: DRHD: handling fault status reg 2
May 29 13:04:28 precision7810 kernel: [ 3974.676467] DMAR: [INTR-REMAP] Request device [00:00.0] fault index 1d [fault reason 38] Blocked an interrupt request due to source-id verification failure
```

One solution, but not satisfying is to hit Ctrl + Alt + F1, log on and type "unity --replace". But then I have to log on again and I loose everything that was on the way.

I saw similar issues where people modifies GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub but it doesn't seem to work for me (or I didn't try the right value). It was initially set to "quiet splash" and now I have set "quiet splash nouveau.modeset=0" but I'm not even sure to know what I'm doing. At least it's not worse :)

[This case]("https://lists.fedoraproject.org/pipermail/users/2016-January/468326.html") concerning Fedora seems really close to what happens to me, but couldn't solve my problem.

Something that might be linked (or not): I had another issue before (the first one was already there) with my video card. The driver installed by default was "radeon" and I had some crashes with an image processing application, regarding memory. I saw a fix on [AMD's webpage]("http://support.amd.com/fr-fr/download/workstation?os=Linux%20x86_64#release-notes") in the last AMDGPU driver, so I switched from radeon to amdgpu and it seems to work fine.

But I still have these OS crashes :(
If anyone has an idea on how to fix this, I would really appreciate!

---

### Post by altersedrik on 2018-02-06
Hey there,

Did you ever find a solution to your problem? I am on a Dell Precision Tower 7910 and this keeps happening to me. Originally I was on Ubuntu 14.04, then I re-installed on 16.04 to no avail. The computer just freezes at some point (quite frequent, I'd say daily), then I can still go to the TTY1-6, but if I then switch back to Unity (ctrl-alt-f7), it completely crashes and I have to hard reboot.

This is a big problem for me as this is the lab computer, which I insisted for a long time to move to Linux, and now it is completely unreliable. 

I understand this problem is probably linked to the graphic card FirePro 4100.. I have tried to install the driver from ATI, but it prevents me completely from loging in, so I uninstalled it.

Any hints?

Best,
Sedrik

---

### Post by mörgæs on 2018-02-06
The hardware is so new that one can't be sure that semi-old software like 16.04 supports it completely. 

I would recommend that you try 17.10.1 in a live boot to see if it's more stable.

---

### Post by scpsc on 2018-02-12
Hi,

I still got the issue, on a daily basis like you. As morgaes says, I want to try with a newer version to see if the hardware is better supported. Live boot is an option, but as the crash is quite random, I can't spend one or two days working on a live boot and I will just reinstall as soon as I have time to do so.

Good luck

---

### Post by peter-vavra-1984 on 2018-04-17
Hi, 

did you happen to find a way to fix this?

I think I have the same issue (also random crashes, not clearly related to what I'm doing) on a machine on both Ubuntu 16.04 LTS and 17.10 (I upgraded a while ago). 

What I noticed is that I have a similar CPU/GPU setup, although not identical:
dual Xeon E2620v4
Sapphire GPro 4200

I'd be happy to properly debug this, but I do not really know where to start.. 

best,
Peter

---

