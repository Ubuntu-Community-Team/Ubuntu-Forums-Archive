---
title: "Ubuntu 14.04.4 LTS 64 session flashback (metacity) and libreoffice bug"
date: 2016-02-25
forum: General Help
---

### Post by erotavlas on 2016-02-25
Hi,
I'm using Ubuntu 14.04.4 LTS 64 bit with 4.2.0-30-generic kernel and gnome session flashback (metacity) and libreoffice installed by adding the latest ppa via
```

sudo -i add-apt-repository ppa:libreoffice/ppa -y

```
The following command gnome-shell --version returns GNOME Shell 3.10.4
I have a problem when I'm using libreoffice tool highlight color. When I use it, the topbar with applications, places, etc... and the footer bar disappear as in the attached screenshoot. I have to log out or to reboot the system. I'm quite sure that this is not related to libreoffice since it happens with current (and previous) version
Version: 5.1.0.3 (5.0.5)
Build ID: 1:5.1.0~rc3-0ubuntu1~trusty0 (5.0.5~rc2-0ubuntu1~trusty1)
CPU Threads: 4; OS Version: Linux 4.2; UI Render: default; 
It happens only with metacity but does not happen with compiz. At the moment I'm using the last one. I think that is related with ubuntu and session display manager.
Any suggestions? Is it a bug to report?
Thank you

---

