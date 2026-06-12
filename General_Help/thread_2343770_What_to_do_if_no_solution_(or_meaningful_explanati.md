---
title: "What to do if no solution (or meaningful explanation) through Forum or Launchpad"
date: 2016-11-18
forum: General Help
---

### Post by lister171254 on 2016-11-18
Trying to find out what to do if the issue you find is neither resolved in the Forum nor in Launchpad

I've found an issue with my Laptop with a Hybrid card

[https://ubuntuforums.org/showthread.php?t=2341016](https://ubuntuforums.org/showthread.php?t=2341016)

I also reported this issue in launchpad

[https://bugs.launchpad.net/bugs/1637032](https://bugs.launchpad.net/bugs/1637032)

I appreciate that support is on a volunteer basis, butiven the lack of a potential solutions, my question is: What next?

I know I can reinstall 16.04LTS, but given the fact the the problem is easily reproduced (well, at least for me), by booting the 16.10 Live CD, there is clearly no clean way forward for me unless somebody figures out what the problem is.

---

### Post by Bucky Ball on 2016-11-18
I'd reinstall 16.04 LTS and follow the bug report with 16.10 and see if anyone else jumps onboard. If someone else reproduces it, you have a bug. 

16.10 has been out about, what, a month? I only use LTS and not usually until a month or so after release. You could try 16.10 again in a month or two and see if there's an improvement. If everything was working in 16.04 LTS, any big difference? You'll be installing 17.04 in April if you choose to go with 16.10 anyhow, so unless you have a good and specific reason (the reason for many is that their hardware is so new it will only work in the latest release and that doesn't seem to be the case here). 

As for where's next, once you've posted around the Ubuntu support forums and posted a bug, not sure there is a 'next'. How good are you in a terminal and troubleshooting things of this nature? :-k

(... and hello from 29C sunny Adelaide. ;))

PS: If you have the room, just install 16.04 LTS on another partition so you can keep playing around and updating 16.10. I have three (I think) installs at the mo and a couple of partitions for virtual machines. Multiple installs can use the same /swap partition (and /home if you want to go that way. Silly question, but you did a full update/upgrade on 16.10 after install? You have 'Canonical Partners' repo on?

```
sudo apt update
sudo apt full-upgrade
```

---

### Post by cariboo on 2016-11-19
Have you tried booting with the nomodeset option? You can set it by pressing F6  at the menu screen when booting from the live CD. I use an older Nvidia card and haven't suffered from the same problem as you, but I have seen other posts about the same problem.

You may want to add the output of:

```
 inxi -G
```

to your bug report. The more information you can give the devs the better. Bugs take time to solve, if you aren't getting action on you bug report, maybe send Brian Murphy and email, and make sure you give him as much information as possible.

---

### Post by lister171254 on 2016-11-19
Thanks for your quick reply
Yes. Will probably re-install 16.04 as I need this Laptop for work

Given the LiveCD has the same problem, I don't think I bother with an additional partition.
I've been in IT for quite a while, so am ok with using a terminal

(Hello from not so sunny Sydney too)
Thanks

---

### Post by lister171254 on 2016-11-19
Thanks cariboo.

Will post the additional output on Launchpad.
Also, I should have been more precise. I don't even get to the menu screen when booting from the LiveCD without the screen flashing! 
So when it asks you if you want to try Ubuntu, the screen flashes

Thanks

---

### Post by ian-weisser on 2016-11-19
Since Canonical's engineering effort is on Mir/Unity8 to completely replace xorg, I doubt the professional engineers will have much time to patch xorg. However, Debian gurus may be interested, and Xorg devs may be interested.

The bug should be marked as a Regression: in the title and with a #Regression tag.
Take a look at the Bug Triage Guide [https://wiki.ubuntu.com/Bugs/Triage](https://wiki.ubuntu.com/Bugs/Triage) to see what else you can do to get your bug more likely to be fixed.
You should scan the 414 other xorg bugs in Launchpad for a duplicate report. Debian bugs, too. And Xorg upstream bugs.

It takes a bit of effort to get a bug fixed in this community. I have done it several times. 
Sometimes, you must investigate and Triage the bug fully yourself. Appoint yourself the coordinator and expert on that single bug. Identify, link, and upstream the bug across all the bug trackers. Clarify poorly-worded reports from other sufferers in the wilderness and bring them into the bug ('me too!').
You must make it super-easy for the dev to understand the problem. They fix the problems that they understand.

---

### Post by lister171254 on 2016-11-19
OK. Tagged as Regression.
Given that this problem (also) occurs when booting the LiveCD, but before actually running Ubuntu, I'm somewhat at a loss where to start.

---

