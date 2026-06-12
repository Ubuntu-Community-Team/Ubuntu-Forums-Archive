---
title: "Latest Xorg version spiking CPU usage, causing lockups."
date: 2007-01-23
forum: General Help
---

### Post by Lukian on 2007-01-23
Since the last Xorg update, it's CPU usage has been spiking to 100% periodically and often causing lockups (requiring a reset) as a result.

How can I backdate Xorg to a previous version or fix this issue?

I can provide more information as needed.

---

### Post by Godzig on 2007-01-24
I'm having a similar problem but xorg starts around 10% of CPU and gradually creeps up to claim 70%-80% and shuts everything else out. takes an hour or so though, not an instantaneous spike.

---

### Post by VoodooDali on 2007-02-03
This problem is driving me nuts. My computer is nearly inoperative, because my CPU is hovering at 100% continually.

So far I have tried the following, to no avail:

. Checked for the correct driver in Xorg.conf (i810 - correct).
. Disabling the "composite" option in Xorg.conf.
. Turning off the system tray, GUI effects and all eye candy (although none of these gave me any trouble before).
. Updating drivers and all other software.
. Reconfiguring Xorg.

I know this much is true (with apologies to Spandau Ballet):

. It's not a distro problem, as I'm seeing it echoed on Gentoo and SUSE forums.
. It's not a video processor or driver problem, as I've seen it happening to ATI, nVidia and other users as well as my Intel "Extreme" (yeah, right) graphics array.
. It's not a KDE thing, as it happens to GNOME users too.

I am convinced the problem is directly traceable to Xorg itself - unfortunately, X.org and the associated Wiki are no help at all.

Just writing this post has taken me a half hour. I'm *this* close to a reinstall, and avoiding all updates until I hear the problem is fixed.

My rig:
. Alienware Sentia series laptop
. Intel Pentium M series, 2GHz
. Intel Extreme Graphics 2 (P.O.S.) video
. 2GB RAM

Your advice would be greatly appreciated.

---

### Post by Godzig on 2007-02-03
I had a setup that was going fine until a recent xorg update then have been experiencing similar problems to yours, though my symptoms are a gradual increase in xorg cpu usage over a few hours until I needed to reboot.  I found that disabling my screensaver in the system menu (which was set only to blackscreen anyways - nothing fancy) actually solved the problem for me. (after a reboot).

There is still the problem of xorg just collapsing on some websites (webmd.com someone previously mentioned) but so far that hasn't caused too much strife for me; yes it happens to me as well and I'm curious if the two are linked...but pretty few websites give me problems.  Maybe flash / xorg trouble?

wish I knew more, but alas -- n00bdom.

---

