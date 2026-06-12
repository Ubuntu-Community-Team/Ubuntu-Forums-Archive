---
title: "Power Management in Xubuntu 14.04"
date: 2015-01-13
forum: General Help
---

### Post by arabian.gabe on 2015-01-13
Hi,

This message is more of an FYI for developers. I am running Xubuntu 14.04 on an older Dell Latitude and no matter how I set my power management options (monitor sleep/off I set to 'never' on both A/C and battery) my system continues to go in to standby mode after a period of inactivity. Looking through the forums I found a thread from 22 March 2011 titled "Monitor goes into standby mode" (posted by cccc), which provided me with a helpful script to stop this from happening. However, every time xubuntubase is updated I have to re-add that script to the Application Autostart list.

This is by no means a deal breaker for Xubuntu as the work around is quite basic. I am simply bringing this up as a bug that needs some attention.

Cheers,
Jeremy

---

### Post by phidia on 2015-01-13
I really doubt any developers are going to see this if you want to make a suggestion or file a bug report you can do that [here]("https://bugs.launchpad.net/ubuntu/").

---

### Post by slickymaster on 2015-01-13
> **phidia said:**
> I really doubt any developers are going to see this if you want to make a suggestion or file a bug report you can do that [here]("https://bugs.launchpad.net/ubuntu/").

xfce4-power-manager are tracked in Xfce Bugzilla so the bug should first be filed upstream, [here]("https://bugzilla.xfce.org/enter_bug.cgi"). Afterwards when filing at launchpad you can link to it in order to keep track of its status. Launchpad will synchronizes the status automatically for you.

---

### Post by Dennis N on 2015-01-13
If it blanks after 10 minutes, could be DPMS acting up. See this thread, post #4,  for a solution:

[http://ubuntuforums.org/showthread.php?t=2253791](http://ubuntuforums.org/showthread.php?t=2253791)

Another case of same problem:

[http://ubuntuforums.org/showthread.php?t=2256459](http://ubuntuforums.org/showthread.php?t=2256459)

---

### Post by arabian.gabe on 2015-01-14
Thanks for the info guys. I will file a bug report at the links you provided.

---

### Post by Dennis N on 2015-01-14
> **arabian.gabe said:**
> Thanks for the info guys. I will file a bug report at the links you provided.

If yours is the DPMS problem, it has been fixed in Xubuntu 14.10 with a new version of xfce4-power-manager.

---

