---
title: "Login Loop - Standard Solutions not working"
date: 2019-01-22
forum: General Help
---

### Post by beenny on 2019-01-22
Hello,

I'm on 18.04 and I'm experiencing a login loop. My computer froze randomly - this has actually happened another times since upgrading to 18.04. I did a hard reboot and tried logging in. I get a flash of my desktop, the screen goes black and then i'm back on the login screen.

I've tried:

* Checking x-authority ownership (no problem)
* checking /tmp permissions (no problem)
* i've reinstalled lightdm (no dice)
* i've installed gbm3 and uninstalled lightdm (no dice - previously both were installed)

I've uploaded a screen shot of my xession-errors but I don't really know what I'm looking for.

Any thoughts would be greatly appreciated. I don't really want to have to reinstall my system.

Thanks,

Ben

---

### Post by l4a-hf0 on 2019-07-19
Hi beenny.  I realise you posted this back in January, so you must've figured things out by now :).   I recently experienced a login loop.  Like you, I followed two of the above-mentioned so-called standard remedies, and neither worked.  I wasn't in the mood to install lighted or re-install gdm3, and kept looking for another solution.

I eventually did manage to get rid of the login loop, but I still am not clear on the exact mechanism of how I fixed it.  

From what I understand, it's got to do with Wayland which does the same job as Xserver/X11/Xorg etc.  Ubuntu ships with Wayland _but I've been reading that it's actually disabled by default_.   I personally didn't know about Wayland until I found myself needing to diagnose this login loop issue, and over the course of doing the research I encountered this thing called Wayland.  

Yet, it appears that it was an explicit disablement of Wayland, by editing the file /etc/gdm3/custom.conf,and uncommenting the line #WaylandEnable=false, that I believe fixed the issue.

For me the issue occurred quite suddenly, after I had issued several apt-get install and apt-get update commands.  I went back into my apt install history (/var/log/apt/history.log) and narrowed it down to one particular software package that I had installed shortly before the issue arose.  I un-installed that package via apt-get purge and rebooted.

After reboot, I was able to log in and things so far appear to be back to normal.

So, I would say that it's possible that Wayland is actually ON by default and some software I installed didn't work well with it

---

