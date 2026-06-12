---
title: "Acer AO 722 stopped booting from SSD"
date: 2012-12-31
forum: General Help
---

### Post by tarkawebfoot on 2012-12-31
I've been working with my AO 722 for a few months now with only a few problems. One of these problems is that the sound never worked. This post [http://bernaerts.dyndns.org/%20http:/bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722]("http://bernaerts.dyndns.org/%20http:/bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722")
suggested upgrading to the 3.4 kernel to fix the problem so I tried it. It did indeed fix the problem for about a week.

The the day before yesterday, it just stopped booting. Symptoms are, when cold booting, immediately after the bios startup, I get an LSD-ish patchwork of colors. Virtual consoles don't work, or at least I can't see if they do. There's nothing to do but reboot.

It boots from the Live USB just fine. No video problems at all. But if I reboot from the Live USB and remove the USB, it goes into an infinite reboot cycle. If I cold boot again, I get the symptom above. I can find nothing in syslog that looks like a problem.

I've tried removing the 'nomodeset' kernel option and restoring it. I've tried downgrading to the 3.2 kernel. I've tried the 3.2 kernel with and without the nomodeset option. I've also tried uncommenting the line in the GRUB cfg to enable the GRUB console. Nothing changes.

Attached is my boot info script results. Any help appreciated.

---

### Post by tarkawebfoot on 2013-01-05
Well, I found no solution at all anywhere. Fortunately Ubuntu fixed itself. Last night I chroot-ed in and did an apt-get update/upgrade and found that there was an update to Grub.

I crossed my fingers, installed it and rebooted. Problem fixed. I'm back on the 3.2 kernel and all seems well (except no sound of course).

I had done an update-grub when switching back to the 3.2 kernel but it didn't fix the video problem.

So this begs the question: what did the update of Grub do to fix the problem? Is there any way to examine the sequence of events that run when Grub is updated through apt-get? A post install script perhaps?

Brian

---

