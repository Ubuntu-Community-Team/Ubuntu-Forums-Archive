---
title: "How best to run the GA kernel?"
date: 2023-03-03
forum: General Help
---

### Post by donald187 on 2023-03-03
I'm on a fresh install of Ubuntu 22.04 on a Dell Inspiron 3910.  I've been on Ubuntu for about 6 months with the 5.15 kernel and the sound has worked fine.  

When the 5.19 kernel got installed the sound started having problems.  The test button in sound settings would sometimes not work.  And on YouTube the videos would not play sound but if I paused for 45 - 60 seconds then played again the sound would work.

This seem to be a kernel problem as I had similar problems on Debian on kernels higher than 5.15 but less than 6.1. (The symptoms started off different but changed to be similar in Debian as the Backports Kernel changed.)   Sound worked on a 5.15 kernel.  The problem was eventually solved in the 6.1 kernel.  So I suspect the same will be true on Ubuntu.

[https://forums.debian.net/viewtopic.php?f=10&t=152359](https://forums.debian.net/viewtopic.php?f=10&t=152359)

At the moment what I've done is to uninstall the HWE kernel and installed the GA kernel according to the following two links

[https://ubuntuforums.org/showthread.php?t=2468665](https://ubuntuforums.org/showthread.php?t=2468665)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

The second link says 

> 
It is advised to keep Ubuntu Desktop 20.04 LTS with the kernel flavour  picked during installation. It can be either HWE or OEM flavour.  Changing to track GA kernel may result in regressions of performance,  hardware support, and certified features


Is this a real problem?

The same page says the preferable way to be on the GA kernel is to install Ubuntu 20.04 and then upgrade to 22.04.  To do that I'll have to disable Secure Boot (I've tried it).

The page may or may not say that you can install 22.04.1 and then update to stay on the GA kernel.  Actually it seems to not say this but I thought I'd bring it up.

So it's a problem to manually install the GA kernel.  But it's a problem with Secure Boot to do it the right way.

Asking the impossible question,..., is there a best way?  Or something I haven't thought about?

---

### Post by guiverc on 2023-03-03
I've experienced no issues with the documentation page you listed

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Ubuntu 20.04 LTS Desktop was the first Ubuntu Desktop release that defaulted to using the HWE kernel stack for all media (*flavors of Ubuntu still vary as per 18.04 & earlier LTS releases, with 20.04 & 20.04.1 media using GA & 20.04.2 & later defaulting to HWE*), thus that documentation uses 20.04 in its examples, but just replacing 20.04 with 22.04 should work  (*I've tested it, but not recently*).

FYI:   If you read the document, it tells you to install the other GA stack first, then test it.. ie. you're doing the test with both GA & HWE kernel stacks installed; and you can keep your systems this way (I do!), as it tells you only when happy to remove the unwanted stack. ie. the removal of the second kernel stack is somewhat optional.

If both stacks are installed, which will mean more disk space used (esp. /boot), and you'll have both stacks being updated so more bandwidth will be used, but the extra disk space & bandwidth used is minimal except if using a *metered or expensive internet connection* or *very small drive storage*.

Also note:  The use of some kernel modules (esp. nvidia) can prevent both GA & HWE (and/or OEM) stacks from co-existing.

The ^ above was written with a partial *misunderstanding* of your question.

The documentation you quoted about installation choices refers specifically to Ubuntu Desktop ISOs using the `ubiquity` installer, as it has the capacity to install GA, HWE or OEM depending on what it determines is best for the device as recognized during installation.  Depending on what media you installed with, your ISO may or may not have any of this *logic*, eg. no *supported* Lubuntu (*a flavor*) ISO contains more than a single stack, with the ISOs for 22.04 & 22.04.1 having GA, and 22.04.2 & higher having HWE which is the *default* for *flavors*.

No actual setting is made as to which kernel stack(s) are installed; the difference is just which packages are installed (ie. if you were using GA + HWE at 20.04 and *release-upgraded* to 22.04, your upgraded *jammy* system will have both installed).  Most of the OEM kernel options are selected because of OEM testing & them speaking with Canonical & recommending a specific setup choice (ie. there is reason for it), but not all hardware is covered by these agreements and personally I don't have any hardware that's installed with an OEM kernel (*thus have no device where I could explore further with it*).

---

### Post by donald187 on 2023-03-03
> **guiverc said:**
> I've experienced no issues with the documentation page you listed

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Ubuntu 20.04 LTS Desktop was the first Ubuntu Desktop release that defaulted to using the HWE kernel stack for all media (*flavors of Ubuntu still vary as per 18.04 & earlier LTS releases, with 20.04 & 20.04.1 media using GA & 20.04.2 & later defaulting to HWE*), thus that documentation uses 20.04 in its examples, but just replacing 20.04 with 22.04 should work  (*I've tested it, but not recently*).

FYI:   If you read the document, it tells you to install the other GA stack first, then test it.. ie. you're doing the test with both GA & HWE kernel stacks installed; and you can keep your systems this way (I do!), as it tells you only when happy to remove the unwanted stack. ie. the removal of the second kernel stack is somewhat optional.

If both stacks are installed, which will mean more disk space used (esp. /boot), and you'll have both stacks being updated so more bandwidth will be used, but the extra disk space & bandwidth used is minimal except if using a *metered or expensive internet connection* or *very small drive storage*.

Also note:  The use of some kernel modules (esp. nvidia) can prevent both GA & HWE (and/or OEM) stacks from co-existing.

The ^ above was written with a partial *misunderstanding* of your question.

The documentation you quoted about installation choices refers specifically to Ubuntu Desktop ISOs using the `ubiquity` installer, as it has the capacity to install GA, HWE or OEM depending on what it determines is best for the device as recognized during installation.  Depending on what media you installed with, your ISO may or may not have any of this *logic*, eg. no *supported* Lubuntu (*a flavor*) ISO contains more than a single stack, with the ISOs for 22.04 & 22.04.1 having GA, and 22.04.2 & higher having HWE which is the *default* for *flavors*.

No actual setting is made as to which kernel stack(s) are installed; the difference is just which packages are installed (ie. if you were using GA + HWE at 20.04 and *release-upgraded* to 22.04, your upgraded *jammy* system will have both installed).  Most of the OEM kernel options are selected because of OEM testing & them speaking with Canonical & recommending a specific setup choice (ie. there is reason for it), but not all hardware is covered by these agreements and personally I don't have any hardware that's installed with an OEM kernel (*thus have no device where I could explore further with it*).
I get the feeling that on that document page I listed that the GA kernel is not "optimized" for that version of Ubuntu.  But everything seems to be working fine with the GA kernel.  Is that all that matters or will problems arise later, for example, during an update?

I torrented the iso using the link from the alternative downloads page

[https://ubuntu.com/download/alternative-downloads](https://ubuntu.com/download/alternative-downloads)

and created it with Gnome Disks on Debian on a usb stick.

---

### Post by guiverc on 2023-03-04
Ubuntu Server installations default to the GA kernel stack, as it's the more *stable* option, with *stability* prized on servers.

Ubuntu Desktops default to the HWE kernel stack as it provides a newer *graphics stack* coming from the newer non-LTS releases, as desktop users tend to want the *latest* kernel modules (aka *drivers*), the default of HWE provides this.

I'm not aware of any optimization differences; as the GA kernel stack is chosen for *stability* as the Ubuntu Kernel team have to support it for 5 years just counting *standard support *(it's longer if you include ESM).  The non-LTS kernels used in HWE are only supported for ~9 months though the final HWE kernel is the GA kernel from the next LTS release.

Personally I've found some older hardware performs better with older kernels, thus with GA providing the oldest kernel for a given LTS release; it can be perform better; but these sort of experiences are very hardware specific (*and the difference is usually related to the graphics stack*).

---

### Post by donald187 on 2023-03-04
You caught me ready to post so I already have my question. :)

> **guiverc said:**
> 
I'm not aware of any optimization differences; as the GA kernel stack is chosen for *stability* as the Ubuntu Kernel team have to support it for 5 years just counting *standard support *(it's longer if you include ESM).  The non-LTS kernels used in HWE are only supported for ~9 months though the final HWE kernel is the GA kernel from the next LTS release.


What about this?  Is this the "optimization"?  Does this happen at installation?
> 
Canonical maintains multiple kernel packages for each LTS version of  Ubuntu, which serve different purposes. Several of the kernel packages  address the need for kernels with specific performance priorities, for  example, the low-latency kernel package. Others are focused on  optimisation for a particular hypervisor, for example, the kernel  packages which are named after public clouds. You are recommended to use  the [detailed Ubuntu kernel guide]("https://wiki.ubuntu.com/Kernel") to select the best Ubuntu kernel for your application.


[https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle](https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle)

Could this be what the following is referring to?
> 
It is advised to keep Ubuntu Desktop 20.04 LTS with the kernel flavour  picked during installation. It can be either HWE or OEM flavour.  Changing to track GA kernel may result in regressions of performance,  hardware support, and certified features.


[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by guiverc on 2023-03-04
> **donald187 said:**
> You caught me ready to post so I already have my question. :)

What about this?  Is this the "optimization"?  Does this happen at installation?

[https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle](https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle)

Could this be what the following is referring to?



Yes there are optimized kernels (eg. low-latency), but I'd suggest staying away from them unless your specific use-case requires them (*or they were installed by a `ubiquity` installer from an ISO that included that option; as I've stated I've not got any hardware where I've seen this so haven't explore it much*).

I have had no need for optimized kernels like low-latency (*thus have little experience*), but I am aware that many Ubuntu Studio users can benefit from *low-latency* for audio/video production, but the Ubuntu Studio team have still suggested most users use the *generic* kernels as they'll experience fewer problems with them (*using low-latency only when required when workload requires it*).  As I'm not a Ubuntu Studio user, my retention from reading their blogs would have been less than someone using the product so I'd check for clues before relying on my memory.

As for your final quote; I sort of covered that with my reference to `ubiquity`.  I'm very aware of what kernel stack I expect installed for a given release; gaining that detail from 
- release (22.04), 
- desktop (HWE if 20.04 or later), server (GA) or flavor (GA for <.2 & HWE for >=.2)

If I didn't know, I could always look up the manifest of packages that I'd expect installed (eg. for Ubuntu Desktop 22.04.2 LTS I'd view [https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.manifest](https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.manifest) and look at the defaults; I'd see
```

linux-generic-hwe-22.04	5.19.0.32.33~22.04.9
```

so if my install was something different (*excluding just an updated kernel due to normal upgrades; here I'm talking about a 5.15 GA kernel stack, or an OEM kernel*) I'd assume that `ubiquity` or the desktop installer for that release made such a change. I have insufficient knowledge here to advise, but I'd likely assume the kernel it installed & I had was the correct one for my hardware.

My 2c.

---

### Post by donald187 on 2023-03-04
Ok, thanks!  It sounds like I'm ok to stay on the GA kernel.  I actually did run 

```

dpkg --list "linux-*" | grep 5.19

```

and

```

dpkg --list "linux-*"

```

before I uninstalled anything and the list in the manifest was what I got so it looks as if I'm ok.

Thanks again!

---

### Post by donald187 on 2023-03-04
I suppose there may also be standard performance improvements with higher versions of kernels.  But this wouldn't be "optimizing" as such.  But I doubt that the documentation would warn users away from the GA kernel on this basis.  I don't know.  Maybe it would make a difference with new computers?  Just thinking out loud.

[https://www.makeuseof.com/tag/update-linux-kernel-improved-system-performance/](https://www.makeuseof.com/tag/update-linux-kernel-improved-system-performance/)

---

