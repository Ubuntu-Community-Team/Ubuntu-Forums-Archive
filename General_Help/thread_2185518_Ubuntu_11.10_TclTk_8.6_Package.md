---
title: "Ubuntu 11.10 Tcl/Tk 8.6 Package"
date: 2013-11-03
forum: General Help
---

### Post by mikecomaroto on 2013-11-03
I found tcl/tk 8.6 packges on [https://launchpad.net/ubuntu/+source/tk8.6](https://launchpad.net/ubuntu/+source/tk8.6) and [https://launchpad.net/ubuntu/+source/tcl8.6](https://launchpad.net/ubuntu/+source/tcl8.6).

How do I update my repository so I can issue "sudo apt-get install tcl8.6*" and "sudo apt-get install tk8.6*"?

Thanks.

---

### Post by fantab on 2013-11-03
Is there a reason as to why you are still using 11.10? Ubuntu 11.10 has reached its 'End Of Life', if you don't already know this then see [HERE]("https://wiki.ubuntu.com/Releases"). 11.10 is not supported anymore and the repositories won't work.
It is recommended that you upgrade to latest version of Ubuntu, that is still supported.

---

### Post by mikecomaroto on 2013-11-03
Yes, I was finishing my master's thesis and didn't want any problems since I already had all my files, code and settings just how I needed them. I've been putting off the uprgade.

---

### Post by fantab on 2013-11-03
I think you should upgrade to next version 12.04. Since its an LTS version it is supported until 2017. It might work for you as its the next version from 11.10. [Read Here for a how to]("https://help.ubuntu.com/community/EOLUpgrades").
Or If you have a partition to spare then you can install the latest version of Ubuntu to it and eventually migrate all your data to it.

**Back up all your important data first**, perferably to an external device.

Those repositories won't work with your version of Ubuntu.

---

### Post by Bucky Ball on 2013-11-03
If you are doing more study I would stick to the LTS versions. They are intended for production machines, servers, and any machine required to be solid and stable for a long time. 12.04 LTS is supported until 2017 and is a one click upgrade to 14.04 LTS when it comes out next April, or you can wait until 16.04 LTS in April 2016. The upgrade via the Update Manager should preserve settings, etc. also. So going from 11.10 to 12.04 LTS is my recommendation.

Open Update Manager, hit 'Settings' at bottom left, click the Updates tab and at the bottom, set the notification for 'Long Term Releases'. Your only issue is that it might not work because 11.10 repos are down, but I remember this working okay for another user not long ago. 

If you're now going on to do your PhD or professional work, stay with LTS. You do not want to be dealing with unexpectedly having to  tweak newer releases and they are only supported for nine months from here on in (as opposed to LTS five years). I know the situation you are in because I have been at it for seven years myself and about to start my masters next year (or have a year off probably).

Good luck! 

PS: I always have the LTS as my main squeeze and two spare partitions for playing around with other releases/distros, when I have the time or inclination. I can always fall back on the LTS, doesn't matter what breaks with the others.

---

### Post by mikecomaroto on 2013-11-05
I just finished my upgrade to 12.04 LTS. It was easier than I thought. I backed up everything before of course just in case. I was glad my boot loader didn't revert to my windows partition boot loader and stayed grub.

So now that I've upgraded, how do I solve my original post? I still can't issue a sudo apt-get command and I really don't want to compile tcl/tk (I know how, but I prefer the package installs).

Thanks.

---

### Post by mikecomaroto on 2013-11-05
Thanks for the advice on the upcoming updates. I made the jump to 12.04 with few annoyances. Except my Ambiance theme font colors are all messed up but I worked around those issue from searching the web. I've been using Linux for years but whenever I find a comfortable setup I like I usually see no reason to change.

---

### Post by Bucky Ball on 2013-11-05
Great news! You are set now and can jump from LTS to LTS as you wish and have five years support besides. Good luck with all future plans. ;)

---

### Post by mikecomaroto on 2013-11-05
I think I've answered my own question from [http://www.ubuntuupdates.org/package/core/precise/main/base/tcltk-defaults](http://www.ubuntuupdates.org/package/core/precise/main/base/tcltk-defaults).

Looks like I'll have to go with ActiveTcl or just compile.

Thanks guys for the help!

---

### Post by mikecomaroto on 2013-11-05
Thanks man! Good luck with your master's. I completed mine while I was already working so if that's your situation stay organized and drink a lot of coffee!

---

### Post by Bucky Ball on 2013-11-05
Bad news, I don't drink coffee (or tea)! 

To help others, you might like to mark this thread as solved by following the instructions in my sig. And thanks for that. Think I'm going to take a year off to remind myself I have a life before I start I've decided. After seven years part-time, it would be nice to not always have the feeling that something is due! ;)

---

