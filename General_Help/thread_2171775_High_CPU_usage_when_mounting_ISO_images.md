---
title: "High CPU usage when mounting ISO images"
date: 2013-09-01
forum: General Help
---

### Post by kmyst01 on 2013-09-01
I'm using Ubuntu 12.04 and I'm in the process of setting up a PXE server.  I had booted up with max_loop=64 appended to my grub cmdline to give me more loopback devices so I could mount a large number of ISO images.  After adding the information in /etc/fstab and issuing a mount -a command my system immediately shot up to 100% CPU usage with a process gvfs-gdu-volume-monitor as the culprit.

I let it run for ~1 hour and it never went down.  The only solution (aside from killing the process) is to umount all the volumes I had just mounted.  Google has pointed me to a large amount of launchpad bugs for older releases and the best I've been able to determine is that the process gvfs-gdu-volume-monitor is what causes drives to appear in the sidebar in Nautilis.

Mounting each ISO via loopback one by one whilst monitoring in another window with top shows me that each successful mount triggers the process for a brief second then it drops off.  However, after 9 mounts, the 10th mount causes the system to ratchet up to 75-85% usage and remains steady at that amount.  Further mounts worsen the issue.  Dropping back to at least 9 mounts removes the problem.

So....after a couple days of tinkering and google searching I've just about given up.  Anyone have any ideas?  All the reports I've come across aren't directly related to loopback mounting a large number of ISO images.  Mainly attaching a USB hard drive or RAID rebuilds or just high CPU usage when logging in.  This is kind of a deal breaker for setting up a large number of images for PXE.

---

### Post by kmyst01 on 2013-09-03
Not sure what the problem was but it's fixed now.

---

