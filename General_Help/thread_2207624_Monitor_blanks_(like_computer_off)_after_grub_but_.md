---
title: "Monitor blanks (like computer off) after grub but only sometimes"
date: 2014-02-24
forum: General Help
---

### Post by darakus on 2014-02-24
Greetings,

I have a desktop computer which dual boots Windows and Linux. I have run Fedora for quite some time now but I wanted to try Ubuntu. So I installed Ubuntu via a USB drive and everything installed successfully. However I am having an intermittent problem during boot. Sometimes (50% of the time or greater) when I'm booting, after grub my monitor will go blank and it will say hdmi no signal as it does just after I power off my computer normally. The monitor acts as if the computer is off. This behavior is the same whether I use hdmi or dvi connections to monitor. I've had the same result with both Ubuntu 13.10 and Ubuntu 14.04.

If selected in grub Windows still boots up and works properly, as did Fedora before Ubuntu. Also, I'd like to add that when Ubuntu does properly boot everything works fast and flawlessly and I really enjoy using it. So I'd like to figure this out, it seems like one of those little linux problems where you tweak one tiny thing and it fixes the problem forever.

I'm using a AMD Radeon HD 7970 with the open source driver. It's always worked well for non game workloads in the (recent) past.

I apologize if I didn't post enough information, I am just not sure where to look and don't want to post useless log files. Any suggestions to try to resolve this problem or ways that I might troubleshoot to get to the bottom of this would be very helpful.

Thanks for any help you can give.


UPDATE:
I just wanted to update my post with the solutions I've tried this morning. I've tried the three workarounds in this document [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen). None of them fixed my problem, but I did get a little bit more information. After removing quiet and splash from the kernel command line I was able to see that sometimes KMS would get enabled before the blank screen and sometimes the blank would happen before KMS (I can tell because when KMS kicks on because my monitor goes to native resolution).

So I'm thinking this is happening because of some race condition during boot, but I'm still not sure what to do next.

UPDATE2:
I tried the proprietary AMD driver and the result was the same. Sometimes a blank screen after grub, sometimes it worked. So I'm guessing the problem lies elsewhere. Another thing I might point out is I am using a solid state drive. I know these are getting very common these days, but I'm wondering if the increased data read speed might be causing a race condition to break my boot sometimes. From my past experience that seems unlikely, but I'm at a loss here.

SOLUTION: [http://ubuntuforums.org/showthread.php?t=2210142](http://ubuntuforums.org/showthread.php?t=2210142)

---

### Post by grahammechanical on 2014-02-24
> [COLOR=#000000]it seems like one of those little linux problems where you tweak one tiny thing and it fixes the problem forever.[/COLOR]

Do not bet on it. I see this problem as something we have to live with. The loading process goes from Grub to the Xserver, to LightDM (Light Display Manager) which should show a splash screen to the login screen, and on to Compiz (Compositor/window manager) and then to the desktop user interface. And in the process Linux is loaded and we are logged in as a user and then Ubuntu/Gnome is loaded on top of Linux.

Yes, at some point the video signal is stopped and our monitor displays a No Signal message. I guess that this happens when the loading process needs to switch from the basic video modes used at the start to the optimum video mode as recorded in the monitor's EDID (Extended Display Identification Data).

I am surprised that it works as well as it does. But things are getting better. By Ubuntu 14.10 or 15.04 Ubuntu will be running on MIR which will replace Xserver, LightDM and Compiz.

Regards.

---

