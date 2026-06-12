---
title: "Kernel panic for single session, others work"
date: 2014-09-05
forum: General Help
---

### Post by JKyleOKC on 2014-09-05
Yesterday I added a few lines to my ~/.gtkrc-2.0 file in an attempt to widen the grab area for resizing windows, then logged out and back in. During the login, the system froze with the capslock and scroll LEDs blinking. I had to force power off to regain control, but after rebooting and cleanup of the disk it still froze after logging in with the same condition. This time, however, it got part-way into my (apparently saved) xubuntu session before the freeze.

Several months ago I created a second user on this box while troubleshooting some other problem; after several attempts to reboot into my main user I tried the second user, and got into the system okay. I was able to verify that the files in my main user's home directory seem unaffected -- and also that I could use the "switch user" choice on my Action button to get into my main account without the freeze!

I subsequently removed the changes I had made to the gtkrc file, logged out completely, re-booted, and tried my main account. It still froze. After yet another reboot I tried switching sessions to "xfce session" and that got me into the system -- but with the mouse pointer invisible. The desktop was still responding as I moved the mouse, but no pointer appeared on screen. Logging out and back in using the alternate account brought back the pointer, and "switch user" got me back into my main account with the pointer still visible.

From all this, I've concluded that something messed up a saved session in my main account to cause kernel panics after Orage begins to load, if using "xubuntu session" but not if using "xfce session" or if logging into the alternate. However I've not managed to locate that saved session in order to eradicate it!

I'm running Xubuntu 12.04.4 with all updates installed, plus the xfce 4.10 manager from the PPA in order to get past the "CPU Graph" applet's bug. Video is Nvidia GeForce 6150SE nForce 430. FWIW, one network adapter vanished at the same time as this happened; it was the one driving my LAN and does not show at all in /var/log/syslog for all the reboot attempts. It does appear at one point early in the boot sequence, but never again. I would expect an actual hardware failure to affect all accounts equally, rather than just one kind of session in a single account, though.

What I'm looking for are suggestions on tracing down the true cause of the apparent kernel panic at such a strage location in the boot/login sequence, and ways to stop it from happening. All ideas are welcome!

[COLOR="#FF0000"]EDIT: After posting initially I rebooted, used the -65 kernel, and had no problem at all getting into the main account. I then rebooted again, using the -68 kernel, and again no problem. Don't yet know whether the problem is gone for good, so still need ideas for troubleshooting.[/COLOR]

---

### Post by JKyleOKC on 2014-09-06
Bump. The mouse pointer problem seems worse, the machine is slowing down, and in general it seems time for a re-install -- but first I must back up nearly 400 GB, and I still have no idea what the root cause might be...

---

### Post by JKyleOKC on 2014-09-09
Quick status update -- backup is approaching the 200 GB point and estimates 36-50 hours yet to go. Using USB external drive and getting less than 1 MB/sec average transfer rate!

---

