---
title: "missing files when Ubuntu 14.04 and Windows 10 share the same partition"
date: 2016-02-06
forum: General Help
---

### Post by m3esha on 2016-02-06
Hi.

I've been using Ubuntu alongside Windows for years now, always using biggest NTFS "media partition" on both OSes. However, since I upgraded my Windows to 10, I have an issue.

Every time I download something to this partition while using Windows, after reboot Ubuntu has an issue with mounting this partition saying it's corrupted. I can easily fix it using ntfsfix, but almost always some data gets lost in the process. It's also missing later on Windows.

Same goes the other way: every time I download something to this partition while using Ubuntu, some data gets lost when logging to Windows. Windows reports disk issue (or it doesn't) and tries to fix it. Usually it fails: says it was a success but some data gets lost. I think for now it's really successed twice (on 50 attempts or so).

As a result I stopped using this partition on Ubuntu but it sucks and I'd like it back.

During Windows upgrade I had an issue ([http://ubuntuforums.org/showthread.php?t=2288988&p=13330797](http://ubuntuforums.org/showthread.php?t=2288988&p=13330797)). After attempt described in this thread, second one went with no problems. Maybe it's related.

Sorry if this was already brought up, I didn't find such case.

---

### Post by lisati on 2016-02-06
Others might be able to elaborate, but I've heard that Windows 10 introduced some new-fangled suspend/hibernate mode which can mess with your ability to access partitions from another OS. I believe one solution is to shut down Windows completely rather than a regular "restart" and then boot into Ubuntu.

---

### Post by m3esha on 2016-02-06
Thanks for a suggestions but I almost always shutdown completely going from Windows to Ubuntu (sorry if my previous post was unclear about that) so it can't be that.

---

### Post by Mark Phelps on 2016-02-06
> **m3esha said:**
> Thanks for a suggestions but I almost always shutdown completely going from Windows to Ubuntu (sorry if my previous post was unclear about that) so it can't be that.

That doesn't matter -- even when you shut down, unless you have gone to the trouble to disable FastStartup in Win10, it will STILL go into hibernation.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by m3esha on 2016-02-06
Is there any drawback? Since I am to disable something called "FastStartup" I guess after this change it's going to boot slower (significantly?) and that's all?

Thank you for your help, I'll give it a shot later today.

---

### Post by Vladlenin5000 on 2016-02-06
Yes, that's all.

Here's the thing: Windows always had boot problems and the newer versions are no exceptions. Instead of fixing the underlying cause(s), Microsoft decided to masquerade the symptom. That's FastStartup in a nutshell.

---

### Post by m3esha on 2016-02-06
Worked perfectly, thanks!

And as for the boot speed, I didn't even notice any change.

---

### Post by Vladlenin5000 on 2016-02-06
> **m3esha said:**
> And as for the boot speed, I didn't even notice any change.

Running in a fairly recent and/or powerful hardware I wouldn't expect anything else.

---

