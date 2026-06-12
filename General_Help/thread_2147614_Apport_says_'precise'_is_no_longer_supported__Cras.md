---
title: "Apport says 'precise' is no longer supported?  Crash issues.  12.04 LTS"
date: 2013-05-22
forum: General Help
---

### Post by bruti on 2013-05-22
I am not sure where to put this.  I will be browsing the internet with firefox and get a message "System Problem" and prompt me to report the issue.  When I do, Apport pops up and directs me to [www.ubuntu.com/support](www.ubuntu.com/support) (or some website like this).  I can't see the error report when I try to view it.

My system will slow down, and eventually freeze.

I am not sure what is causing this issue.

---

### Post by dino99 on 2013-05-22
That is where logs can help you to find usefull warning(s)/error(s)
Glance at : ~/.xsession-errors  & /var/log/
When a crash happen, Apport try to report that issue on bugs.launchpad.net  (but you need to open an account there first) and the crash file is inside /var/crash/

---

### Post by bruti on 2013-05-22
Here's my crash log.  Not too sure what's going on.

```
xserver-xorg-video-intel.2013-05-22_12:27:54.794444.crash   xserver-xorg-video-intel.2013-05-22_12:52:24.940243.uploaded
xserver-xorg-video-intel.2013-05-22_12:28:00.052202.crash   xserver-xorg-video-intel.2013-05-22_12:58:18.939250.crash
xserver-xorg-video-intel.2013-05-22_12:52:24.940243.crash   xserver-xorg-video-intel.2013-05-22_12:58:24.343553.crash
xserver-xorg-video-intel.2013-05-22_12:52:24.940243.upload  xserver-xorg-video-intel.2013-05-22_13:02:21.507537.crash


```

---

