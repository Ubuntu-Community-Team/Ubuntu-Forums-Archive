---
title: "Update dependency issue causes network and video drivers not to load"
date: 2019-09-17
forum: General Help
---

### Post by colehill on 2019-09-17
I had spent a couple of weeks or so getting an 18.04 desktop  installation to my liking on my old Fujitsu tower and it was working well.
I came to it one morning and it was showing an update alert icon at top right.

> [INDENT]The following packages have unmet dependencies:  linux-headers-generic-hwe-18.04:
Depends: linux-headers-5.0.0-27-generic but it is not installed linux-image-generic-hwe-18.04
Depends: linux-modules-extra-5.0.0-27-generic but it is not installed
[/INDENT]


I went through several different help articles, trying various fixes to get the update to complete.

Somewhere in the process I have ended up with an installation that doesn't load the video or network drivers - possibly the motherboard chipset.  In Windows terms it is booting into safe mode - with default video and no network drivers.

Please advise how I can get out of this?  Is there some kind of rollback operation (System Restore), or a way of redetecting the drivers?

TIA

KD

---

### Post by TheFu on 2019-09-17
In non-Microsoft environments, a "System Restore" is called "a backup" and you are responsible to making it BEFORE it is needed.

At every boot, Linux re-detects all hardware.  If you stay within Canonical's repos for APT, update and upgrade weekly, then it is hard to get into dependency problems.  If you manually install any .deb file or use any 3rd party PPAs, then it is easy to get into dependency issues.  If you manually load drivers, expect to have to re-re-reload them manually with every kernel change.

Ubuntu LTS releases have an "Additional Drivers" tool somewhere. I don't use the GUI for this, so I don't know where it is.  I don't use the GUI for any patch management. It is too slow.

So, the first things that need to be done are:
```
sudo apt update
sudo apt upgrade
```
Do those two commands at least once a week.  Best to make a backup just before doing it. If either has warnings or errors, fix those immediately.  Running those commands **AND** confirming that you have, will set a baseline for any more troubleshooting.

There are probably 50 different backup tools. What you backup is up to you.  Linux expects users to know what is important.  "Everything" usually isn't the best answer.  With good backups, you can install a fresh system, restore the system settings, system data, personal settings and the most important personal data within about 45 minutes at most.  Restoring huge personal data that is 100GB-50TB will take longer, but the core OS and your settings will all be there, working, quickly.  Unlike Windows, linux only needs about 6G-10G for most OS installations.  Everything after that amount is "cheese", optional.

Also, the output from **lsb_release -a** would be helpful. Here's mine:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial

```
Please use 'code tags' like I have and show the command with the output.

Remember, we can't know anything that you don't specifically tell us.  Ubuntu is 1000x more complex than most people know. Accurate, correct, details matter.

---

### Post by SeijiSensei on 2019-09-17
When you boot the machine, do you have an Advanced option?  You should be able to revert to the previous kernel.  See if that solves the problem in the short run. But then make sure to run
```

sudo apt update
sudo apt upgrade

```
Read the text that upgrade displays carefully.  You might need to use "dist-upgrade" to insure you have the correct kernel and associated files.

If you see errors that suggest using "sudo dpkg --configure -a" or "sudo apt install fix-broken" try those first.

---

### Post by colehill on 2019-09-17
> **SeijiSensei said:**
> When you boot the machine, do you have an Advanced option?  You should be able to revert to the previous kernel.  See if that solves the problem in the short run. But then make sure to run
```

sudo apt update
sudo apt upgrade

```
Read the text that upgrade displays carefully.  You might need to use "dist-upgrade" to insure you have the correct kernel and associated files.

If you see errors that suggest using "sudo dpkg --configure -a" or "sudo apt install fix-broken" try those first.

Thanks, unfortunately I think "sudo apt update" is going to require internet access - and the network drivers are not loading.

It was the sequence of dpkg and fix-broken commands that seem to have caused the problem, the initial issue was only an error message on a usable system.

I will try for the Advanced option, but I haven't noticed one.

KD

---

### Post by TheFu on 2019-09-17
> **colehill said:**
>  
I will try for the Advanced option, but I haven't noticed one.

KD

2-3 older kernels should be available on any Ubuntu, if not more.  Drivers are tied to the kernel, so using the prior kernel to find and fix issues is good.  If a new kernel failed to install correctly, there are a few likely issues. Often, it is an out-of-storage problem in /boot/.

---

