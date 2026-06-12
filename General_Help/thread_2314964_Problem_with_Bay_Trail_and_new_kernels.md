---
title: "Problem with Bay Trail and new kernels"
date: 2016-02-25
forum: General Help
---

### Post by jicha on 2016-02-25
Since the release of Ubuntu 16.04 LTS is approaching, I would like to bring to attention a serious bug which affects all Bay Trail computers and causes a complete system freeze. The bug is described here: [URL="https://bugzilla.kernel.org/show_bug.cgi?id=109051"]https://bugzilla.kernel.org/show_bug.cgi?id=109051
[/URL]
What does it mean? Computers running Ubuntu 14.04 LTS with 3.13 kernel work fine. Once they get upgraded to 16.04, they will freeze within a couple of minutes.

I think this is a very serious bug and should be fixed before Ubuntu 16.04 LTS is released. I hope Canonical has enough power to push Intel to fix their broken driver.

---

### Post by Bucky Ball on 2016-02-25
*Thread moved to **Ubuntu Development Version**.*

Everything and anything to do with unreleased development versions goes here. Thanks.

I am running 16.04 LTS on a brand new desktop with an Intel i7 6700 processor and an Nvidia GTX 970 GPU using Blender to edit video (or test doing so). Faultless, but Haswell, not Baytrail, and I notice the majority of problems on that thread coming from folk using Celeron processors. You would be looking to run Xubuntu or Lubuntu on a Celeron processor at this point I'd think. Does this bug apply to them also, it applies to the actual Ubuntu kernel all flavours are built on?

I have no crashing after a few minutes (or a couple of hours). In fact 16.04, not suprisingly on new hardware, has better hardware support and is running smoother than 15.10 which has been pretty much a nightmare for me (about to install 14.04 LTS on that machine to see if that improves things until 16.04 LTS is official in April).

16.04 is a development release though, so who knows. Maybe something related to this bug will jump up and bite me on the bum while I'm looking the other way. Thanks for sharing the info. ;)

---

### Post by dino99 on 2016-02-25
Many times it has been discussed/reported dist-upgrade problems: 14.04 -> 16.04
This is due to "transition" problems not managed (yet/unknown); so a valid Bay Trail testing is about a fresh install only (for the moment at least)

---

### Post by jicha on 2016-02-25
Bucky Ball> The problem is valid only for computers with Intel bay trail chipset. It is present in all releases since 15.04, maybe even 14.10. But it will hit many more people when 16.04 gets released. People running LTS release want stability. But if this bug isn't fixed soon, all people with bay trail computers will have an unusable computer after the upgrade.

Since the problem is in broken Intel driver directly in kernel, it affects all *ubuntu versions, in fact all Linux distributions.

dino99> This has nothing to do with dist-upgrade. There is a bug in Intel graphics driver for i915 (found in bay trail chipset) which causes a freeze usually after a few minutes if using HW acceleration or playing video. It affects also current non-LTS releases.

---

### Post by grahammechanical on 2016-02-25
It would be nice if members of the Ubuntu kernel team were to participate in this forum. But I doubt if any of them do. We can contact the Ubuntu kernel team directly.

[https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)

Some of those who frequent the Ubuntu Development Section of this forum like to test kernels on the development release before they are put in the main Ubuntu update channel. How many of them are running Bay trail CPUs I cannot say. But not having the hardware does limit the testing of the development release. But there are threads on this section of the forum relating to each release candidate kernel.

There may even be a Ubuntu bug on Launchpad about this very problem. Yes, checking launchpad for a bug would be the way to go, in my opinion. I am confident that the Ubuntu kernel team are aware of kernel bugs registered on bugzillar. It must be part of their terms of employment to know what's happing to the Linux kernel.

[https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)

> The submitter should provide as much information as possible in the bug description: 


[LIST=1]
[*]The majority of kernel bug** are hardware specific** so be sure to note what hardware/device is being used. 
[*]Document any known steps to reproduce the bug. 
[*]Also note whether the bug exists in previous kernel versions of Ubuntu or if it's a regression from previous kernel versions. 
[*]Finally, it's critical to also make sure **to test the latest development Ubuntu kernel version** as well as the [latest upstream mainline kernel]("https://wiki.ubuntu.com/KernelMainlineBuilds"). 

[/LIST]


Before upgrading or even putting a fresh install of a new Ubuntu release we should read the release notes.

Regards.

---

### Post by jicha on 2016-02-26
The bug is mentioned here: [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1531865"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1531865
[/URL]
But nobody really cares about it. There is a workaround with kernel command line parameters. But an average user can not do it and they won't know that they should do it.

I'm not reporting a new unknown bug. I just wanted to highlight this problem which will IMHO affect a lot of users (all with bay trail chipset) after upgrading to 16.04 LTS. It seems that everybody is happy with partial workaround and nobody really tries to fix it.

---

### Post by shivam-19mishra on 2016-04-26
I confirm the problem. Any kernel above 3.19.xx freezes the system completely. 

There's no solution that I have found as yet. I use an HP r250 tu intel pentium quadcore processor.

---

### Post by jicha on 2016-04-26
You could try the workaround with max cstates = 1. It might work for you. Unfortunately it doesn't for me. I will have to stay at 14.04 as long as possible and then I will probably throw the computer away. I doubt it will ever get fixed.

---

### Post by shivam-19mishra on 2016-04-27
I did try that, it has till now worked for me. cstate 1 does the trick for me. I'd be testing it for some more days and then would like to proceed to the 16.04 LTS update. I think the workaround works well for N3540 processors.

Though there still are some messages during boot up related to intel soc DTS; I searched on that and that seems to be WAY tougher thing to solve, it's developer level stuff, moreover, it's not a bug so I will let it be.

---

### Post by cariboo on 2016-04-27
Moved to General Help, as this thread now has nothing to do with Yakkety.

---

### Post by bswarm2 on 2016-04-27
I set max cstate=1 in the bios, absolutely no more crashes.

---

### Post by QLee on 2016-04-27
This is what I have about the "Bay Trail", it is not an exclusive Ubuntu problem. I needed to do it on a Debian install also, however the system did not freeze as much on a Debian Stable kernel, but there could likely be some difference between mainboards. It does appear to be being looked at, link below.

The "Bay Trail" processors and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have those random freezes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. Remember what you have done so you can remove it once they deal with the problem.

If you encounter random freezes on a board that has one of those processors try adding intel_idle.max_cstate=1 to the GRUB line that boots your system. I wouldn't use it on any other family of processor. You can find a list at: [http://ark.intel.com/products/codename/55844/Bay-Trail](http://ark.intel.com/products/codename/55844/Bay-Trail)

For example: in the file /etc/default/grub  
change the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" 

and then ```
sudo update-grub
```, reboot to use it. Test by opening a terminal and entering: ```
cat /sys/module/intel_idle/parameters/max_cstate
```, it will return a number.


It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

Remember what you have done so you can remove it once they deal with the problem.  <-------- Remember this.

---

### Post by vgerris on 2016-08-21
what do you mean this is not a bug? It most certainly is. The issue does not occur on Windows. This is clearly a bug that somehow poppud up in the 3.16 line of kernels after some changes related to cstate code.
It would help if people keep trying to focus on how this can be fixed on who needs to be reached to get it done.
Both intel and Linux kernel devs prefer these rampant bugs to not be present.
So keep an eye on :
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
and try to reach out to intel and kernel devs.
I did, let's see where it goes.
The cstate workaround works for me but uses more power. check the bugzilla bug for more workarounds.
There is NO solution YET.
cheers

---

### Post by vgerris on 2016-09-04
seems there may be light on the end of the tunnel:
[https://bugzilla.kernel.org/show_bug.cgi?id=109051#c437](https://bugzilla.kernel.org/show_bug.cgi?id=109051#c437)
Cause seems to be a hardware bug. I had contact with some intel people and I will try to keep pushing until a fix ends up in the kernel.

---

### Post by yonnie on 2016-11-04
I have a zotac nano that kept freezing under 14.04LTS.  I changed it to 16.04LTS and the problem is now worse.  I ordered a pre-built pre-installed computer and it froze so often, it was not usable.  Both computers were Baytrail quad core.  When is this problem going to get addressed?

---

