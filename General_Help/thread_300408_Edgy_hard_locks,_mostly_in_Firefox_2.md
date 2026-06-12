---
title: "Edgy hard locks, mostly in Firefox 2"
date: 2006-11-15
forum: General Help
---

### Post by Robb Kidd on 2006-11-15
Running Edgy with the latest updates, upgraded from Dapper the canonical way (gksu "update-manager -c").  nVidia GeForce FX 5200 with nvidia-glx running dual LCDs.

Various different interactions with Firefox will lock-up the computer: clicking on a link, scrolling down a page, in the process of installing an extension.  I've not found a consistent action that will cause this.  It only ever locks when I am interacting with Firefox, but the bulk of my time on this computer is spent in a browser window so I'm not sure how telling this symptom is.

And by lock-up, I mean the screen goes black and then the monitors power down from signal loss. CTRL-ALT-F1 does not take me to the first virtual console.  CTRL-ALT-BACKSPACE does not kill and restart X.  The Caps Lock key gets no response on the keyboard LED and the machine is unreachable over the network.  The machine must be powered down and started again to work until the next lock-up.

I used to have a variety of things installed and have since removed them: beryl is no longer running and the Flash plugin was removed.  Per some other advice on the net, I added [export XLIB_SKIP_ARGB_VISUALS=1]("http://ubuntuforums.org/showthread.php?t=286069") to firefoxrc and [upgraded nvidia-glx to v1.0.9626]("http://www.nvnews.net/vbulletin/showthread.php?t=76493&page=2").  The machine still locks up when interacting with Firefox in some indescribable manner.

Has anyone experienced this?

---

### Post by Robb Kidd on 2006-11-17
So, I nuked this computer and reinstalled from an Edgy Desktop CD.

I have added nothing beyond the default install and still have system hard lock issues while in Firefox.  And because it hard locks, I have no idea where I might look for an error log or how to call a debugger.

---

### Post by doobit on 2006-11-17
A hard lock usually points to a hardware problem. Linux is multi-tasking, so applications tend to be able to run independantly even when one other one locks up for some reason. Firefox uses a few more resources for different processes than some other programs - it's a little "heavier" so some process that it's doing is locking it up by stressing some hardware - maybe a hard drive.. Try opening it from a terminal and move the terminal to one side and the Firefox browser window to the other side of your desktop. That way you will still be able to see the error when it locks up. Even better, do the above and also open a second terminal and run top at the same time.

---

### Post by Robb Kidd on 2006-11-17
Thanks for the reply, doobit.  

When the machine hard locks, the display gets powered down from a loss of signal from the video card.  The lock-up is not that the display is frozen; it is that there is no more display.  Nonetheless, I tried the terminal windows as you suggested and was not able to catch anything odd before the screen went dark.

I think I may revert to Dapper.  I did not have this problem before the upgrade to Edgy.  If I continue to have this issue, it will certainly point to a hardware problem.

---

### Post by doobit on 2006-11-17
OK, by lockup, usually we mean that the display is frozen and the mouse and keyboard no longer function. If your display goes black, then that's a different thing and may point to a video driver problem or some other problem with Xorg, or your video card itself.

---

### Post by Robb Kidd on 2006-11-17
Alrightie.  Apologies if I used misleading terminology.  The symptoms from my original post remain, though. 

In addition to the blanking screen:
[LIST]
[*]Nothing happens with CTRL-ALT-BACKSPACE: X does not quit and restart.
[*]Nothing happens with CTRL-ALT-F1: the first virtual console does not appear.
[*]Caps Lock gets no response on the keyboard LED.
[*]The host is unreachable over the network: no ssh, no pings.
[/LIST]
While the origin might be X, the video card (nVidia GeForce 5200) or the video card driver (occurs with both Xorg's nv and nVidia's nvidia), it is not *just* the screen going blank that's at issue.

I'm reloading Dapper as I type.  I'll see if the problem occurs with the older system installed.

---

### Post by Robb Kidd on 2006-11-17
*sigh*  Dapper's doing it, too.  Time to scrounge a new video card,  I figure.  Thanks for your time, though, doobit.

---

### Post by n8bounds on 2006-11-19
> **Robb Kidd said:**
> *sigh*  Dapper's doing it, too.  Time to scrounge a new video card,  I figure.  Thanks for your time, though, doobit.

PC Hardware is just unreliable.  I'm starting to have the same problems on my old laptop.  It will hard lock with no keyboard response seemingly randomly.    It was a good learning opportunity, though.  The XFS filesystem is very resilient.  It's journaling is very robust, aparently.  What card did you replace your old one with?

---

