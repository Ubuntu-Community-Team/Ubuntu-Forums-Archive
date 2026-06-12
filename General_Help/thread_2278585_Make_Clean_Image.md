---
title: "Make Clean Image"
date: 2015-05-17
forum: General Help
---

### Post by stryker719 on 2015-05-17
All,
I dove off the deep end (for a Windows user) and bought a new Dell XPS 13 Developer Edition.

How do I make a full backup/image of my Ubuntu install?  The idea would be if I break my system somehow, I can load up the clean image and be running just fine in no time.  I know how to do this with Windows, but I've never tried on Linux.

Thanks!

---

### Post by ian-weisser on 2015-05-17
> **stryker719 said:**
> How do I make a full backup/image of my Ubuntu install?  The idea would be if I break my system somehow, I can load up the clean image and be running just fine in no time.  I know how to do this with Windows, but I've never tried on Linux.

Welcome to Ubuntu.
We hope you have fun.

The short answer to your question is to use the backup/restore utility included with Ubuntu: System Settings --> Backups

A rather longer answer to your question is that backup strategies are sometimes different in a Linux environment. You need not backup any of your applications from the Ubuntu repositories, nor the OS itself - you can replace them all, for free, anytime you need using either your recovery media or the generic install media from downloads.ubuntu.com. Ubuntu is *designed* to be easily installed on a wide variety of strange equipment. Also, most things you might break can be rather easily *repaired*, so reinstalls are less common than you might think from cruising these help forums. Generally, you need only backup your data and personal settings in your /home directory.

It gets more complex when you start trying to backup system customizations and non-Ubuntu software...but those affect more than just backups anyway (that's why they are 'complex').
I keep thing simple: I back up only my /home (data) using the provided backup application. Everything else is trivial to repair, replace, or reinstall.

If you want to experiment with breaking your system, a Virtual Machine is highly recommended. VM snapshots are a very fast way to recover!

---

