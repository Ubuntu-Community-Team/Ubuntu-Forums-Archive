---
title: "Asus F102B netbook brightness"
date: 2015-09-27
forum: General Help
---

### Post by InverseTelecine on 2015-09-27
I have an Asus F102B netbook with Xubuntu 14.04 on it, and the screen brightness is locked to maximum.

I finally found this thread describing my exact problem, but found no solution:
[http://ubuntuforums.org/showthread.php?t=2213896](http://ubuntuforums.org/showthread.php?t=2213896)

The last post from Toz from March 2014 says: > Found [this entry]("http://www.linlap.com/asus_x102ba")  about your laptop, where the author states that brightness appears to  be broken, yet fixed in newer versions of the catalyst driver (which  unfortunately breaks suspend). Perhaps its best to create a [bug report]("https://help.ubuntu.com/community/ReportingBugs") for this.

I was wondering if there had been any developments on this. I'm using "fglrx-updates (proprietary)" (not sure which version, so see screenshot below) from the Ubuntu drivers menu, but the brightness is still locked. I also don't care about a broken suspend function because I never use it, and I think the few times I have used it it caused a lockup, so maybe that is still an issue. So does anyone know if there have been any developments for just fixing the locked max screen brightness in the past year and 6 months? Thank you.

[IMG]http://i62.tinypic.com/x3px.jpg[/IMG]

---

### Post by DK1993 on 2015-09-27
Have you happened to try X.Org's device wrapper instead of AMD's proprietary driver? The default drivers (FOSS) may support the backlight. Let me know if this helped.

---

### Post by InverseTelecine on 2015-09-28
Thank you for the reply DK. I have tried X.org, or at least the version that is installed by default in Xubuntu 14.04. I didn't even really need to use the proprietary driver, but I was told it might fix the brightness issue. Would a different version help?

---

### Post by sandyd on 2015-09-28
Btw, the bug that was mentioned, and filed has no activity either.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1300499](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1300499)

---

### Post by InverseTelecine on 2015-10-27
Just a few days ago I had to re-install Xubuntu on the Asus F102B, so I thought I'd try vanilla Ubuntu to make sure it wasn't something specific to Xubuntu, which seemed unlikely, but it worked! The brightness controls (even the function hotkeys) work "out of the box" in both Ubuntu 14.04 and Lubuntu 14.04, so I guess it's an XFCE or Xubuntu problem. I wish I'd known about this months ago, but it seemed so unlikely that it would be a Xubuntu problem and not a Ubuntu problem. Either way, Unity is way too much of a resource hog for this little netbook, so I'm running Lubuntu with working brightness controls, and I'm happy with it. I'll say this is solved, even though I do still like XFCE a little better than LXDE. They're both much better than Unity.

---

### Post by InverseTelecine on 2015-10-30
Okay, a big warning for others: what I just said about using Lubuntu/Ubuntu fixing this problem is still correct, but DO NOT try to install proprietary video drivers! Not even to try them out! Just use the X.Org one as activated by default!

I had been happily using my Lubuntu installation on the netbook with working brightness controls for a few days but then thought I'd try to proprietary drivers to see if I could get a performance boost. Big mistake! I installed the "AMD graphics accelerators from fglrx-updates" driver and rebooted and the brightness was again stuck at maximum and nothing would change it. "No problem" I thought. "I'll just switch back to the X.Org wrapper." But no! I switched back, rebooted, and my brightness controls are still broken! I've tried a few of the grub configuration file solutions that others had suggested that I tried before, but no luck.

I'm so mad right now. It's back to hurting my eyes with its ultra-bright screen. Ugh. I'm just going to re-install Lubuntu again, and all my programs, everything. Sigh.

---

### Post by InverseTelecine on 2015-12-03
Sorry to resurrect an older post, but for anyone else with this sort of problem this really seems to be a Xubuntu specific issue; not an XFCE issue. I installed [Ubuntu Studio ]("http://ubuntustudio.org/")(14.04) which uses XFCE and the brightness controls work (although I'm NOT going to try installing the proprietary driver.) If anyone else likes XFCE and has a machine with this problem you could try Ubuntu Studio; it runs very well on the underpowered F102B. For the record, I also tried [Ubuntu Gnome]("http://ubuntugnome.org/") (Gnome 3) and the brightness controls also worked fine, but the little F102B netbook can't handle Gnome 3 very well. It works, but is very slow.

---

