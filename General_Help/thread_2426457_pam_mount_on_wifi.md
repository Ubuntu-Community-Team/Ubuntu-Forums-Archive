---
title: "pam_mount on wifi"
date: 2019-09-09
forum: General Help
---

### Post by hedd.linux on 2019-09-09
For the past several years, I have been using pam_mount to auto-mount Windows Server 2008 and Synology NAS shares when students and teachers log in. This has been successful on desktops running Ubuntu-Mate 16.04 and 18.04, using an ethernet connection.

Now I'm trying to re-purpose Chromebooks which have gone End-of-Life, using GalliumOS 3.0. When I connect via wifi (set up with Network Manager), drives do not mount, with the auth.log file reporting "lightdm: (mount.c:76): mount error(101): Network is unreachable". When I plug in a USB-Ethernet adapter, the drives mount perfectly on login.

This would indicate the pam_mount function is occurring before the wifi is connecting. Is there some configuration option to have pam_mount wait till there is a connection instead of just failing?

Thanks.

---

