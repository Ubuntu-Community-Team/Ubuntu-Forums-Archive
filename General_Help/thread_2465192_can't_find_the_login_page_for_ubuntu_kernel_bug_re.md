---
title: "can't find the login page for ubuntu kernel bug reporting"
date: 2021-07-24
forum: General Help
---

### Post by essin on 2021-07-24
Hello,

I have searched in vain for the login page to report a kernel bug.
I have found dozens of pages that describe the process but none of them have a link to the actual bug-reporting site.

Some pages say to report crashes with apport-cli or ubuntu-bug however what I have no report is not a crash but a freeze. apport-cli and ubuntu-bug both say no crash or product not installed, which are both true, but then the tools exit.

I should mention that I flunked my mind-reading course in college and am consequently terminally challenged in that area.

The problem that I need to report is the following:
I had xubuntu 20.04 5.4 installed on my mac mini and everything was working fine but the disk partitioning was messed up. To find it I had to reinstall so I downloaded an installer dvd image.

The new installer installed the 5.8 kernel instead of the 5.4 kernel. After logging in and especially if the system was idle for a few minutes, the gui would freeze. The mouse pointer could be moved but clicking and typing had not effect. The system itself had not frozen; it was possible to ssh and kill the xfce4 process which returned to a working login screen. Logging in again merely reproduced the freeze.

The then downgraded the kernel from 5.8 to 5.4 and now everything works perfectly again. It seems that perhaps the 5.8 kernel is not ready for prime time and perhaps they shouldn't be distributing it automatically to folks who request an installer.

I think the represent a hardware compatibility-related kernel bug and that it should be reported but, as I said, I have been unable to access the bug-reporting system.

Any suggestions would be appreciated.

Thank you

---

### Post by guiverc on 2021-07-24
Ubuntu LTS releases have two kernel options.

The GA stack option is the original 5.4 kernel that Ubuntu 20.04 LTS originally installed with, and is supported the entire life of the product.

The HWE stack option (hardware enablement stack) means the kernel upgrades at 20.04.2 to using the kernel from 20.10, to using the kernel from 21.04 at 20.04.3, etc. until finally stopping when it's using the 22.04 kernel when it reaches 20.04.5.

There is always some *obscure* hardware* combinations* that run better with some kernel stack choice and not the other choice offered for LTS releases.

I'll use Lubuntu install media here as example as I know it, (*and I've forgotten the specific details for Xubuntu as 20.04 was different to prior releases as it included OEM kernel choices*).

Installing Lubuntu 20.04 using either initial 20.04 or 20.04.1 media defaults to the GA kernel stack being used.

Installing Lubuntu 20.04 using 20.04.2 or later media defaults your system to using the HWE kernel stack.

If you install Ubuntu Server; you have the option of selecting the stack at install time; this choice was offered via the media used for most *flavors* or post-install for main Ubuntu and potentially some *flavors* (*I don't test all; I tested Lubuntu, Xubuntu & Kubuntu but only remember Lubuntu reliably*).

Details of HWE can be found at
- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
which includes the commands to install/switch the other stack post-install

To report bugs I'll offer
- [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

It's best if you file on your actual machine using

```
ubuntu-bug linux-generic-hwe-20.04
```

FYI:  We're getting close to the time of the 5.8 kernel being deprecated; and 20.04 systems using HWE will upgrade to using the 5.11 kernel (ie. 20.04.3 upgrade) which occurs on installed systems prior to official release (*official release refers to the ISO release for new installs*).

---

### Post by essin on 2021-07-25
Thanks for the info. I was a bit confused about the hwe since on my system it listed linux-generic, not linux-generic-hwe.
Is everything in the future going to be hwe?
I know that there are others attempting to run on mac hadware. I will file a report by my guess is that it is unknown what part of the new kernel is causing the gui to freeze. One would hope that future releases would not experience this behavior but, not knowing what is causing it, it would be difficult to fix.

I don't think that ubuntu-bug will let me file anything because I have already downgraded to 20.04 with 5.4 kernel.

I'm wondering if I will be stuck on 20.04.1 forever (not that is necessarily a bad thing)?

---

### Post by guiverc on 2021-07-25
> **essin said:**
> I was a bit confused about the hwe since on my system it listed linux-generic, not linux-generic-hwe.
Is everything in the future going to be hwe?


I already said Ubuntu LTS users have 2 stack choices.

- **GA** for those wanting the *stable* option that never changes, or 

- **HWE** for those with newer devices that need later kernels, kernel modules (ie. *drivers*) but want to remain on the LTS base.

The only change is where new  Ubuntu Desktop **installs** of 12.04 to 18.04 defaulted to GA, from 20.04 and up the new default for **installs** is  HWE  (*upgraded systems keep whatever was the default prior to install*). Server installs using `subiquity` now get a choice too pre-install (a benefit of the newer `subiquity` installer used).  

> **essin said:**
> 
I don't think that ubuntu-bug will let me file anything because I have already downgraded to 20.04 with 5.4 kernel.


You'll be able to file bugs on the GA (linux-generic) kernel, as it's supported the entire life of the product, just like prior LTS release of Ubuntu.

Lubuntu installs of 20.04 or 20.04.1 both defaulted to using the GA kernel by default; just as prior LTS released did.

I'm only guessing, but I doubt the kernel is related to the freeze.  A SysRq command asking the kernel to reboot will confirm that; as if the kernel is working normally; it'll respond to the SysRq command given (be it to safely reboot, kill GUI, shutdown etc), though a *kernel module* maybe related; but they're not part of the kernel itself (commonly called *drivers,* and usually don't come from the linux kernel team).

I'm not familiar with modern macs, but the older mac I have does **not** have a SysRq key marked (*but neither do loads of modern dell etc keyboards either; but they usually have it available via Fn key even if unmarked*), so you may need to use an external keyboard to be able to use it.

---

