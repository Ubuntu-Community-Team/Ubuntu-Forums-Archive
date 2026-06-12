---
title: "XOrg Xserver freezes hole system"
date: 2005-05-18
forum: General Help
---

### Post by goldenboy on 2005-05-18
Hi,
I'm using Kubuntu 5.04 on my HP/Compaq NX7000. And got the following annoying behaviour:

In varying intervals the Xorg process claims 100% of the CPU time. And thus the hole system freezes. Login in via ssh remains working and killing the Xserver

```
sudo kill -9 XXX (Xorg PID)
```

works. But terminating the Xserver with any other singal (i.e. 15 - normal termination) does not work.

The problem may be related to the fglrx driver for the ATI graphics card, but I didn't test this till now. I'm using the "normal" ubuntu xorg-fglrx driver...

Attached you find my xorg.conf file...

Syslog does not show any suspicious as far as I can gauge this. Only thing is that udev removes some device node which I'm not aware of their purposes:

```
May 18 11:19:53 localhost udev[26051]: removing device node '/dev/vcs7'
May 18 11:19:53 localhost udev[26053]: removing device node '/dev/vcsa7'
May 18 11:19:53 localhost kdm[7091]: X server for display :0 terminated unexpectedly
May 18 11:19:53 localhost udev[26077]: creating device node '/dev/vcs7'
May 18 11:19:53 localhost udev[26079]: creating device node '/dev/vcsa7'
```

Thanks for any suggestion in advance


EDIT: Just to update the interested. I switched from XOrg to XFree86, but the issue remains... The XServer consumes 100% of the processor time freezing the hole system...  this sucks

---

