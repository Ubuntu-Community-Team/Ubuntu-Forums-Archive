---
title: "Disk space issue"
date: 2020-11-09
forum: General Help
---

### Post by jgwphd on 2020-11-09
My Ubuntu 20.04 desktop hung. I am using a 130GB SSD partition. Rebooted in safe mode and got a storage warning. System monitor showed available space at 5GB. Found SYSLOG files (syslog = 11.6 GB and syslog.1 =61.1 GB) eating up way too much the disk space. I sent both of then to the trash. I did reboot and the system is still 94% full and teetering on the edge. I went to empty the trash using ".sudo Nautilus" shows a path to .local to .share to .trash which has two directories info and files. Both log files were in the files directory under trash.  Before I go any further I have some questions. Is it safe to just delete these files from the trash? (I looked and there is no option to delete them) and how do I do it or what is the best way? or can someone please provide me some guidance to purge my system of these enormous log files and get my disk space back. Thanks!

---

### Post by dinkidonk on 2020-11-09
The log files are not supposed to grow that large, I would suggest you to examine them in order to find out why they have become so large and fix that issue or else it may happen again. I cannot see what the problem in deleting them would be, though.

---

### Post by jgwphd on 2020-11-09
I found a path to them in the shell and deleted some other files I didn't know were there. Now I have some breathing room at 92% full. I am thinking I really don't want to open these large log files and have them crash the system (because I probably be using a lot of storage to open them up). I assume it is safe to just delete them? If so then I'll keep an eye on them and if they start growing again then I'll see what is going on. I think I need to get to a reliable stable system first.

---

### Post by SeijiSensei on 2020-11-09
You don't have to open the files to see their contents. To view the last thousand lines of syslog use
```
tail -n1000 /var/log/syslog
```
You definitely have a problem with your system since syslog should never grow that large on a well-behaved system. My syslog.1 is 163K. Likely there is some repeated error that is filling your log.

Logs are very compressible.  
```
gzip /var/log/syslog.1
```

---

### Post by ActionParsnip on 2020-11-09
You can watch what's going on with
```

sudo tail -f /var/log/syslog

```
You can see what is being written as its been written. May help.

---

### Post by jgwphd on 2020-11-09
I deleted the log files approx 45 minutes ago. I assume the system reinitializes new log files so, as directed, I issued the command  
tail -n1000 /var/log/syslog

and got the following repeating pattern which occupies most of the log (probably 99%) it loooks like every 5 seconds i get a grouping of 4 messages.

Nov  9 10:58:02 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/124/gvfs' failed: Permission denied
Nov  9 10:58:02 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/doc' failed: Permission denied
Nov  9 10:58:02 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/gvfs' failed: Permission denied
Nov  9 10:58:02 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/1000/doc' failed: Operation not permitted
Nov  9 10:58:07 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/124/gvfs' failed: Permission denied
Nov  9 10:58:07 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/doc' failed: Permission denied
Nov  9 10:58:07 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/gvfs' failed: Permission denied
Nov  9 10:58:07 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/1000/doc' failed: Operation not permitted
Nov  9 10:58:12 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/124/gvfs' failed: Permission denied
Nov  9 10:58:12 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/doc' failed: Permission denied
Nov  9 10:58:12 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/gvfs' failed: Permission denied
Nov  9 10:58:12 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/1000/doc' failed: Operation not permitted
Nov  9 10:58:17 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/run/user/124/gvfs' failed: Permission denied
Nov  9 10:58:17 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/doc' failed: Permission denied
Nov  9 10:58:17 jgw-XPS-8930 gnome-system-monitor.desktop[5069]: glibtop(c=5069): [WARNING] statvfs '/root/.cache/gvfs' failed: Permission denied

Any suggestions. Thanks!     ...BTW, I have the system monitor running on one of my dual screens. I'll turn it off an see what happens too.
Ok, I turned system monitor off 10 minutes ago and the repeating grouping of 4 message stopped. I just turned system monitor back on and the messages didn't reoccur until i selected the "File System" panel and then the messages started to appear again.

BTW, System Monitor Preferences for File Systems: the update interval is 5 seconds. I changed interval to 10 seconds and now log messages are every 10 seconds. 
So why is "permission denied" to system monitor?

---

### Post by TheFu on 2020-11-09
First, you can setup logrotate to limit the size of the syslog. 10MB would be huge for 99.999% of users.  The settings are in /etc/logrotate.d/ and fairly easy to understand with the examples in that directory already.

If you run systemd, the /etc/systemd/journald.conf file has similar settings. There is a manpage which explains those settings.

To me, looks like gnome-system-monitor is the problem, so don't use that anymore.  May want to read up on gnome-system-monitor to learn more about this issue or open a new thread about it, since people who would respond to "disk space" problems and GUI problems are different.

---

### Post by jgwphd on 2020-11-09
Many thanks for your help and the tips! I appreciate your insight. BTW Is there "gnome" or "gnome system monitor" support anywhere on the ubuntu forums?

---

### Post by deadflowr on 2020-11-09
> **jgwphd said:**
> Many thanks for your help. BTW Is there "gnome" or "gnome system monitor" support anywhere on the ubuntu forums?

Yes.
Just post new threads about those issues.

---

### Post by jgwphd on 2020-11-09
...ok, post new thread where? under which area of the ubuntu forum?

---

### Post by TheFu on 2020-11-09
> **jgwphd said:**
> ...ok, post new thread where? under which area of the ubuntu forum?

This one is fine.  The issue is with the current title. You want a thread title that is specific to gnome-system-monitor to get the eyes of people who would know about it.  The people already in this thread would likely have tried to help already if they knew anything about it. You need different eyes. The new people you want aren't going to look passed the title before moving on.

I've found the best information about gnome stuff to come directly from the Gnome project.  Google found that.
[https://wiki.gnome.org/Apps/SystemMonitor](https://wiki.gnome.org/Apps/SystemMonitor)

This is a known problem, though yours seems a little different:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-system-monitor/+bug/1786639](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-system-monitor/+bug/1786639)
I'd guess that either snap constraints or apparmor settings need to be tweaked and since you probably didn't change anything, the distro team should make the update.  That's my guess, but I haven't any clue.

---

### Post by jgwphd on 2020-11-09
Thanks. I posted a comment on the bug 1786639. Thanks for the pointer!

---

### Post by xashyar on 2021-05-13
Hi I'm having this issue with the latest 20.04, Is this still an unresolved issue?

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-system-monitor/+bug/1786639](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-system-monitor/+bug/1786639)

---

