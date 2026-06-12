---
title: "Gutsy locks up on resume until I kill X"
date: 2008-02-25
forum: General Help
---

### Post by chadjohnson on 2008-02-25
Over the last month or so, my laptop has been just about locking just about every other time upon resume. When I look at top/htop output, my CPU is at 100% usage, and memory and swap usage are far less than 100%. However, top/htop do not show what process(s) is (are) using that much of my CPU. Usually only up to 10% is being used. I can still move the mouse, and I can (very, very slowly) do things.

I've looked through syslog and dmesg plenty of times, but I've found nothing helpful. I've also disabled Compiz-Fusion (even uninstalled it), tried suspending and then resuming without the wireless card plugged in, updated the ATI proprietary drivers, disabled and removed Tracker. I don't want to add noapic or acpi=off to my kernel parameters because it makes the wireless and suspend/resume not work. I've also Googled extensively but have found no solutions.

I am not posting in the laptop section because I am not sure this is a laptop-related issue.

My computer is an Acer Aspire 5050, with 1GB RAM, 2GB swap space, Trendnet PCMCIA card, Turion 64 single-core processor.

Any ideas why this happens?

---

### Post by Crafty Kisses on 2008-02-25
Post the following output:
```
top
```

---

### Post by chadjohnson on 2008-02-25
Here is htop output

[IMG]http://chadjohnson.ath.cx/htop.png[/IMG]

---

### Post by chadjohnson on 2008-02-26
This is causing me grief. I will pay $10 USD via PayPal to whoever gives me a working solution.

---

### Post by chadjohnson on 2008-02-26
bump--$10, anyone?

---

### Post by rapiscan on 2008-02-26
This is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/)

The fglrx drivers cause Gutsy  to crash during resume of hibernation / sleep.

---

### Post by chadjohnson on 2008-03-03
Hey, thank you for the lead...it has given me many other leads.

I believe this issue may possibly be an issue with kswapd not waking up, as described [here]("http://groups.google.com/group/linux.kernel/browse_thread/thread/910c08e97eb0357e") (that page is linked to from the link you gave).

I recompiled a new kernel but was unable to boot without acpi=off. I did not think to turn off the splash screen before to get details on why before I switched to OpenSUSE. I did, however, make an image of the partition, so sometime in the future I will try again with Ubuntu if OpenSUSE gives me trouble--and I will pay you then.

Thanks for the help!

---

### Post by chadjohnson on 2008-03-04
You may be right. The same stinking thing happens with OpenSUSE, so it seems.

---

### Post by chadjohnson on 2008-03-08
Follow up:

I tried compiling a new kernel and was half-way successful, and suspend seems to work, but it breaks other things in my system (wireless, ethernet, and 3D acceleration). I started another thread on this [here]("http://ubuntuforums.org/showthread.php?t=717766").

I additionally tried running without the fglrx drivers, just using the open source drivers, and when I try to resume I get a blank screen, and the system is locked up (caps lock, tty switching, and ctrl+alt+backspace do not work). I tried the things described [here]("http://ubuntuforums.org/showthread.php?t=303718") to no avail.

I never thought I would say this, but I am heavily considering going back to Windows. This makes me very sad.

---

### Post by chadjohnson on 2008-03-21
Well a week or so ago I finally got Gutsy to run with the Feisty kernel...not sure why this did not work before. I can suspend and resume once or twice, but the second or third time, the computer locks up on resume.

So, I will just say screw suspend for now, use my desktop for work, and wait for Hardy (hoping this is fixed there).

---

