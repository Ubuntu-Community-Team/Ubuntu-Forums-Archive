---
title: "Record video from security camera"
date: 2016-07-18
forum: General Help
---

### Post by 4kh3RAm on 2016-07-18
I have a B/W security camera and it has a RCA output jack.

I have used it with a VCR to record footage.

Can it be used to record on my computer ?

My Tv card has an RCA jack, but do not know if it can be used with the camera.

Is there software I need to be able to record from the camera ?

---

### Post by Bucky Ball on 2016-07-18
The best thing you can do is plug it in and find out what you get. Have you got Cheese or another app you can see video in? Skype?

Plug it in, switch it on, open a terminal and run 'dmesg'. See anything at the bottom of the output? If the machine has recognised a camera open Skype, Cheese, whatever, and see if it will let you select the camera. Post back with your findings.

The other thing your can do is a search for 'ubuntu 16.04 analogue video camera' and see what pops up, try out what you find and let us know what happened if you need more help. ;)

---

### Post by grahammechanical on 2016-07-18
The RCA jack on the TV card, is it input or output? You may need to find a PC expansion card that accepts RCA input. Or some kind of cable converter. Perhaps from RCA to USB. I am just speculating. I have no experience in this area.

Regards

---

### Post by Bucky Ball on 2016-07-18
> **grahammechanical said:**
> The RCA jack on the TV card, is it input or output? You may need to find a PC expansion card that accepts RCA input. Or some kind of cable converter. Perhaps from RCA to USB. I am just speculating. I have no experience in this area.

Regards

Agreed. You need to have a good look at the card and nut out what's going on with the inputs/outputs. You might be able to tell from sight, but if not, get online and find out what's what with the card if you need to.

When you run 'sudo lshw -C video', without the camera plugged in, what is the output, between code tags, please?

---

### Post by 4kh3RAm on 2016-07-18
> **Bucky Ball said:**
> The best thing you can do is plug it in and find out what you get. Have you got Cheese or another app you can see video in? Skype?

Plug it in, switch it on, open a terminal and run 'dmesg'. See anything at the bottom of the output? If the machine has recognised a camera open Skype, Cheese, whatever, and see if it will let you select the camera. Post back with your findings.

The other thing your can do is a search for 'ubuntu 16.04 analogue video camera' and see what pops up, try out what you find and let us know what happened if you need more help. ;)

Here is bottom 33 lines of dmesg.
```

 600.212813]  ffff88006d80bd78 ffff88006d800dc0 ffff880236241b80 ffff88006d800dc0
[  600.212816]  ffff88006d80c000 ffff8802312ed8fc ffff88006d800dc0 00000000ffffffff
[  600.212818]  ffff8802312ed900 ffff88006d80bd90 ffffffff81829a25 ffff8802312ed8f8
[  600.212821] Call Trace:
[  600.212831]  [<ffffffff81829a25>] schedule+0x35/0x80
[  600.212835]  [<ffffffff81829cce>] schedule_preempt_disabled+0xe/0x10
[  600.212837]  [<ffffffff8182b909>] __mutex_lock_slowpath+0xb9/0x130
[  600.212840]  [<ffffffff8182b99f>] mutex_lock+0x1f/0x30
[  600.212844]  [<ffffffff81620c97>] read_descriptors+0x37/0x100
[  600.212848]  [<ffffffff8128cf9a>] sysfs_kf_bin_read+0x4a/0x70
[  600.212851]  [<ffffffff8128c50b>] kernfs_fop_read+0xab/0x160
[  600.212855]  [<ffffffff8120cc18>] __vfs_read+0x18/0x40
[  600.212857]  [<ffffffff8120d1e6>] vfs_read+0x86/0x130
[  600.212860]  [<ffffffff8120df35>] SyS_read+0x55/0xc0
[  600.212863]  [<ffffffff8182db32>] entry_SYSCALL_64_fastpath+0x16/0x71
[  600.212872] INFO: task lsusb:2372 blocked for more than 120 seconds.
[  600.212874]       Not tainted 4.4.0-31-generic #50-Ubuntu
[  600.212875] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.212876] lsusb           D ffff88020341fd78     0  2372      1 0x00000004
[  600.212880]  ffff88020341fd78 ffff88022ac48dc0 ffff880236240dc0 ffff88022ac48dc0
[  600.212882]  ffff880203420000 ffff8802312ed8fc ffff88022ac48dc0 00000000ffffffff
[  600.212885]  ffff8802312ed900 ffff88020341fd90 ffffffff81829a25 ffff8802312ed8f8
[  600.212887] Call Trace:
[  600.212891]  [<ffffffff81829a25>] schedule+0x35/0x80
[  600.212894]  [<ffffffff81829cce>] schedule_preempt_disabled+0xe/0x10
[  600.212896]  [<ffffffff8182b909>] __mutex_lock_slowpath+0xb9/0x130
[  600.212898]  [<ffffffff8182b99f>] mutex_lock+0x1f/0x30
[  600.212901]  [<ffffffff81620c97>] read_descriptors+0x37/0x100
[  600.212903]  [<ffffffff8128cf9a>] sysfs_kf_bin_read+0x4a/0x70
[  600.212906]  [<ffffffff8128c50b>] kernfs_fop_read+0xab/0x160
[  600.212909]  [<ffffffff8120cc18>] __vfs_read+0x18/0x40
[  600.212911]  [<ffffffff8120d1e6>] vfs_read+0x86/0x130
[  600.212914]  [<ffffffff8120df35>] SyS_read+0x55/0xc0
[  600.212916]  [<ffffffff8182db32>] entry_SYSCALL_64_fastpath+0x16/0x71


```

> **Bucky Ball said:**
> The best thing you can do is plug it in and find out what you get. Have you got Cheese or another app you can see video in? Skype?

Plug it in, switch it on, open a terminal and run 'dmesg'. See anything at the bottom of the output? If the machine has recognised a camera open Skype, Cheese, whatever, and see if it will let you select the camera. Post back with your findings.

The other thing your can do is a search for 'ubuntu 16.04 analogue video camera' and see what pops up, try out what you find and let us know what happened if you need more help. ;)

Skype is not in Package Manger.

Thought that was a popular program. ?

---

### Post by Bucky Ball on 2016-07-18
You need to add the Canonical Partners repository. Go to Software and Updates> Other Software and enable it (tick it). The GUI should offer to update when you are closing it. Do so and Skype should be in the package manager, whichever you're using.

If you have no use for Skype other than this, don't install it. Install Cheese. You only want to see if the camera is working. Installing Skype to do so is killing a mosquito with an elephant gun. :)

Advisable not to install from third-party as the version in the repositories has been tested with your version of Ubuntu.

---

