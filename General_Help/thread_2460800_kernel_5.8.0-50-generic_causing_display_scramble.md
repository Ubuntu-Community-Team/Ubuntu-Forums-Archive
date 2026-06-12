---
title: "kernel 5.8.0-50-generic causing display scramble"
date: 2021-04-19
forum: General Help
---

### Post by JamButty on 2021-04-19
After I updated to kernel 5.8.0-50-generic, I started getting severely scrambled displays - missing parts, corrupted text, strobing, blank lines - the works. It was the same for all applications. Then I booted into Windows and found no trace of it. Then I booted into the prior kernel, 5.8.0-49-generic, and again, no problems. I can use that for now, but as soon as the next kernel loads, 5.8.0-49-generic will not be available, at least not directly from the boot menu.

Anyone else having similar issues?

---

### Post by CatKiller on 2021-04-19
I've not experienced the issue, but
> **JamButty said:**
> I can use that for now, but as soon as the next kernel loads, 5.8.0-49-generic will not be available, at least not directly from the boot menu.
this isn't strictly true. The number of old kernels to keep is a configurable parameter (although I don't know off hand where it's configured), and (temporarily) removing the HWE metapackage will stop you getting any new kernels at all until you know that the bug has been fixed. You should file a bug report, if there isn't one already, detailing the regression. Alternatively, you could go the other way, and try a much newer kernel from the mainline repository to see if the issue has been fixed.

---

### Post by ajgreeny on 2021-04-19
Do you have secure boot enabled?
Are you using an nvidia graphics card which needs a driver installed for the new kernel?

If so disable secure boot, install the nvidia driver needed and try again.  Unfortunately Windows updates can, I gather, re-enable secure boot even if you have disabled it in the past, stopping the necessary modules for the driver being installed properly.

---

### Post by JamButty on 2021-04-19
Thankfully, Ubuntu is not paternalistic like Windoze which shoves updates down your throat  with or against your will. I can just decline updates for a while until I see if this is fixed. I seem to remember a few years ago that several ( maybe 5 or 6) kernels used to be offered in the default boot menu.
I found a couple of pages sort of related, but they explain how to set an old kernel as the default, rather than how to expand the menu choices. Also there are very many articles explaining how to get rid of excess menu choices, so this must have been a problem in the past.
I get contradictory info on what kernels are available to me.
One command lists about 22 kernels:
```
sudo dpkg -l | grep linux-image
```
but another indicates there are only two in BOOT
```
ls /boot/
```

---

### Post by JamButty on 2021-04-19
ajgreeny  - Secure boot IS disabled
gpu is onboard (Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller)
Previously, I have never had to dl drivers specific to this.

---

### Post by CatKiller on 2021-04-19
> **JamButty said:**
> Also there are very many articles explaining how to get rid of excess menu choices, so this must have been a problem in the past.
It was. A few releases ago the defaults were to have a smallish EFI partition and to never autoremove kernel packages. Unsurprisingly, as time went on, there were a lot of people with broken systems: the kernel installation couldn't finish because there was no space, so package management was broken, and, in some cases, you couldn't boot because the kernel hadn't finished installing. Nasty. So some versions are kept, but old ones are autoremoved, now.

---

### Post by CelticWarrior on 2021-04-19
> ...[COLOR=#000000]a smallish EFI partition[/COLOR]

I think you mean a smallish /boot partition. The ESP stores .efi files, not kernels.

---

### Post by CatKiller on 2021-04-19
> **CelticWarrior said:**
> I think you mean a smallish /boot partition. The ESP stores .efi files, not kernels.
Could be. I wasn't affected by it (habitually tidying old kernels after I'd checked the new one works), I just saw the people having the issue in the forum.

---

### Post by CelticWarrior on 2021-04-19
With LVM+LUKS the installer typically creates a separated /boot partition and the default size used to be very small indeed.
Normal installations do not have that problem.

---

### Post by grahammechanical on 2021-04-19
> I can use that for now, but as soon as the next kernel loads,  5.8.0-49-generic will not be available, at least not directly from the  boot menu.


Do not use Software Updater for the time being. Use the terminal.

```
sudo apt update
sudo apt upgrade
```

When you have confirmed that that any new kernel does not cause problems, then you can run Software Updater and it will want to remove any old kernels. I would wait until at least two new kernels are confirmed as acceptable. Then both the good, older 5.8 kernel and the later, bad 5.8 kernel can be removed.

Regards

---

### Post by JamButty on 2021-04-19
New winkle. First day back on kernel  5.8.0-49-generic, I had no issues. Now, the second day on it, some of the same issues are happening. While still not as extreme as I had under 5.8.0-50-generic, it is getting worse each hour, so this is becoming a more urgent problem. I have good backups and am willing to reload all, but I doubt that would fix it if problems in either kernel are what is causing it.

---

### Post by JamButty on 2021-04-27
The problem progressed so far that I did a fresh system re-install on Apr 23. After, with the default kernel, 5.8.0-50, scrambling was worse than ever, almost unusable. Fortunately, the second kernel offered was 5.8.0-43. I have run on that kernel for 3 days now with no sign of the scrambling issue. Submitted bug report.

---

### Post by ajgreeny on 2021-04-27
I wonder if you would have more success with the kernel series that came originally with 20.04, if that is the version you are running  which is the 5.4.0-# series.
That will be available through the full lifetime of 20.04 and is currently at 5.4.0-72.

Install that with terminal or synaptic if you prefer a GUI, choose it from grub Advanced menu and see how that works.
If it is good you can then remove the 5.8 series completely and stay with the 5.4 series by also installing the linux-generic package and removing the linux-generic-hwe package.

One step at a time; let's see if the 5.4 kernel runs first then decide where we go from there.

---

### Post by wowotiel on 2021-04-27
I have had bad experiences with Kernels 5.8.0-50 and 5.8.0-49 and my hardware. See[ https://ubuntuforums.org/showthread.php?t=2460766]("https://ubuntuforums.org/showthread.php?t=2460766").
Kernel 5.8.0-48 (but expired) works well for me and also the kernel series 5.4.
I eventually went back to the 5.4 series.
There are some bug rapports regarding inteldrivers: [https://bugs.launchpad.net/ubuntu/+source/linux-meta-hwe-5.8/+bug/1924624](https://bugs.launchpad.net/ubuntu/+source/linux-meta-hwe-5.8/+bug/1924624)

---

### Post by JamButty on 2021-05-01
wowotiel - yes, mine looked a lot like that initially, then got much worse. I note the bug reports claim that 5.8.51 resolves the problems, but is not in the normally accessed repositories. I had better not go that route as I don't really know what I am doing.

ajgreeny
 that sounds like a plan, as far as I understand it, which is not very far.
just to be clear, are these the only installations I would need initially?
----------

linux-modules-extra-5.4.0-72-generic
linux-modules-5.4.0-72-generic
linux-image-5.4.0-72-generic
-------
Then would I need to do anything to rebuild the grub menu to reflect the 5.4.0-72 kernel under the "advanced" entry or would that happen automatically?

-- and if they work well, I would then de-install
linux-generic-hwe-20.04
linux-headers-generic-hwe-20.04
linux-image-generic-hwe-20.04

and install what to replace them?
Clearly, I do not understand how the parts relate/support each other.

---

### Post by JamButty on 2021-05-13
appears resolved by kernel 5.8.0-53

---

