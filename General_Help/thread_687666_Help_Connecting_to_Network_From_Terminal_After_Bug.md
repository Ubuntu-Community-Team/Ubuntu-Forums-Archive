---
title: "Help Connecting to Network From Terminal After Buggy Xorg Update"
date: 2008-02-04
forum: General Help
---

### Post by GenuineXP on 2008-02-04
So with some rather bad luck my mom installed that bad Xorg update from awhile back and now she can't login. I've been trying to help her over the phone to install the latest updates to fix the problem, but she can't even do that because Ubuntu still does not support her wireless network adaptor.

I installed ndiswrapper to fix this issue, but the signal tends to be weak and I have no idea how to get her connected without using a GUI tool like nm-applet or network-manager-gnome. After modprobe'ing the ndiswrapper module, iwconfig still reports that she's not connected (signal strength is 0/100).  Is there a relatively simple way to configure her adapter and get her connected to the network (and therefore the Internet) for an update, or is this basically hopeless?

I appreciate any help. Thanks!

---

### Post by pointone on 2008-02-04
Have you tried:

```
iwconfig eth1 essid X
```

... where X is the ESSID of your wireless network. Your wireless interface may be eth0 or eth2, depending on what other network devices are in the system.

---

