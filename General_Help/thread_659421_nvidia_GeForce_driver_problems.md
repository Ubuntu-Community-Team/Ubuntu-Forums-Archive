---
title: "nvidia GeForce driver problems"
date: 2008-01-05
forum: General Help
---

### Post by dkonrad on 2008-01-05
I'm having several problems with the nvidia GeForce 6xx on my motherboard, and the Samsung SyncMaster 216BW monitor I recently attached to it.

1) In attempting to fix the other problems, I tried to switch from the proprietary driver to the open source driver. Unfortunately, I have *no* image now! :oops:

So, how do I reset it from the command line (recovery mode)?

2) I can't get it to work in digital mode. I've configured it as a 206BW, since there is no option for 216BW in the config list.

3) It won't stick with 1680x1050 resolution. 

Suggestions?

Thanks!
dk

---

### Post by taurus on 2008-01-05
Just run this command from the recovery mode.

```
dpkg-reconfigure -phigh xserver-xorg
```
And you can reboot your machine with

```
shutdown -r now
```

---

### Post by dkonrad on 2008-01-05
Thanks. The dpkg-reconfigure didn't fix it, so I hand edited xorg.conf and changed the driver back to nvidia (from nv) and that fixed it.

dk

---

