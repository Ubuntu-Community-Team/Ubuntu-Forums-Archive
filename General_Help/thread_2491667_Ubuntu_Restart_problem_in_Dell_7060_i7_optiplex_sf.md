---
title: "Ubuntu Restart problem in Dell 7060 i7 optiplex sff"
date: 2023-10-16
forum: General Help
---

### Post by mountainman70 on 2023-10-16
I have been dual booting Windows & Ubuntu for over 10 yrs. I recently bought a Dell 7060 i7 sff with a 256 ssd. I had no problem installing Ubuntu 22.04 mate alongside of W 11 pro. I thought everything was fine until I did a restart in Ubuntu. W 11 restarts every time. Ubuntu restarts but does not start monitor. I tried new DP to DP cable and DP adapter to HDMI adapter to VGA cable but computer will not turn on monitor on Ubuntu restart. A ll monitors work fine on old W 11 & Ubuntu 22.04 HDMI  computer.

Is there a setting in bios I am overlooking or do I need a different video card?

 Thanks for any replies.

---

### Post by MAFoElffen on 2023-10-16
RE: AMD Radeon RX 550 (to remind me laters)

Does it cold boot into Ubuntu fine? Isolating that it is just a restart problem...

---

### Post by mountainman70 on 2023-10-16
Yes grub gives me both options of W 11 or Ubuntu. Ubuntu opens fine from a cold boot. Just restart does not open monitor.

---

### Post by MAFoElffen on 2023-10-16
I'm having a different restart problem with 22.04, where mine reboots to the BIOS Boot menu. Therefore I have to completely shutdown, then cold boot. But just for my Lenovo Laptop. My 5 other machines have no problem.

Logically (in my reasoning): Where these reboot problems come in, is something is not completely shutting down, and leaving something in memory on the reboot.

During diagnosing my problem, I created a pre-reboot.service that called a script to free things up right before the reboot... Maybe it might help you, or at least rule a few things out...
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,20231016
# Name: pre-reboot.sh
# Purpose: To free/dump the swap, pagecache, dentries and inodes, right before the reboot.
# Called by unit: pre-reboot.service
#   Ran as root
swapoff --all # turn off the swap
echo 3 > /proc/sys/vm/drop_caches # free the pagecache, dentries, and inodes

```
I called it from the unit file like I shared in this post: [https://ubuntuforums.org/showthread.php?t=2491062&p=14158905#post14158905](https://ubuntuforums.org/showthread.php?t=2491062&p=14158905#post14158905)

---

### Post by mountainman70 on 2023-10-16
I don't have any experience using script. Can you give me steps on how and where to install it? Always willing to learn.

Thanks

---

### Post by MAFoElffen on 2023-10-17
First, just to make sure it's not a Graphics driver problem, lets verify that is setup and working... 

From a terminal do
```

sudo lshw -C display | grep -E 'UNCLAIMED|product|configuration'
grep . /proc/cmdline

```
Responding using the "Adv Reply" will bring up the Advanced Post Editor, with the extended tool bar. Select the "#" Icon from the toolbar, and past the copied output between the inserted CODE tags... Finish editing your post, then post it.

---

### Post by mountainman70 on 2023-10-17
[                                                      ]("https://ubuntuforums.org/member.php?u=1044547")[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547")  Sorry to take so long to reply but have had family crises to tend to. I got tired of trying to fix this problem and time to ask for refund was over but Co. that I bought it from agreed to a refund. Waiting for a RMA. Decided to try something else and wiped my 1 tb ssd and installed W 11 without ms account and no internet. Restart works every time which I knew it would. Then I installed Ubuntu 22.04 (instead of cloning Ubuntu from another drive) without internet so no updates and no third party. Just a normal install and restart works every time. Could cloning Ubuntu from another uefi drive be the reason the restart would not work in Ubuntu on this Dell 7060?

---

### Post by MAFoElffen on 2023-10-17
It could have... Might have been a bad EFI file(?) or how the old driver was installed/loaded?

IDK...

But I am happy for you, that everything is working for you now!

If now solved, please visit the "Thread Tools" Link to mark your thread as "solved", so that other users can find what worked for you.

---

### Post by guiverc on 2023-10-17
> **mountainman70 said:**
> Then I installed Ubuntu 22.04 (instead of cloning Ubuntu from another drive) without internet so no updates and no third party. Just a normal install and restart works every time. Could cloning Ubuntu from another uefi drive be the reason the restart would not work in Ubuntu on this Dell 7060?

In your initial post you mention Ubuntu MATE, a *flavor* of Ubuntu Desktop; that can have different defaults to Ubuntu Desktop depending in the media used to install (ie. *22.04 & 22.04.1 install the GA kernel stack for Ubuntu-MATE; 22.04.2 & later use HWE stack that is default for all Ubuntu Desktop 22.04 ISOs*). 

 If you're *cloning* the system from another drive, you may get different defaults to what the install media will provide, as you'll get the defaults of whatever media was used to install the *cloned*-*source* drive. Ubuntu *flavors* (such as MATE) and Ubuntu Desktop have small differences on early LTS ISOs (esp. *initial & .1*).

This maybe a tangent to your issue though; I just offer it, as my optiplex 7050 has two of my five monitors dark part way through boot, but those two monitors are connected to my additional graphics card (*taken from a much older optiplex*) and not the onboard GPU, and kernel stack will influence that; but your issue I gather impacts the whole boot cycle.

---

### Post by mountainman70 on 2023-10-18
I am sure every one does not like reinstalling everything on an OS and would rather clone the OS to another drive. So far restart is working as it should.  I now have to continue reinstalling everything in  all three browsers. Time consuming but I believe it was a corrupt file in the HDMI clone that was causing the problem. I really like this computer and the nvme ssd.

---

