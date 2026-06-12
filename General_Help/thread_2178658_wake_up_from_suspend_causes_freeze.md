---
title: "wake up from suspend causes freeze"
date: 2013-10-04
forum: General Help
---

### Post by IYII3r41n on 2013-10-04
I just recently installed ubuntu 13.04 on dell lattitude E6510. I'm using nvidia driver- NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia--310(proprietary, tested). I have 4 gig of ram installed and swap space is 5 gig. My computer will not suspend correctly. It will turn off like it is going to suspend, but upon wake up the system freezes with a black screen, unresponsive keyboard, but the mouse works. Here's what i ran so far...
```

tail /var/log/pm-suspend.log
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Oct  4 06:05:30 EDT 2013: Finished.




```

```

free -m
             total       used       free     shared    buffers     cached
Mem:          3876       2945        931          0        152       1099
-/+ buffers/cache:       1693       2183
Swap:         5173          0       5173



```

Here are the lines in my grub file...

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

```
sudo apt-get remove hibernate uswsusp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'hibernate' is not installed, so not removed
Package 'uswsusp' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


Can anyone steer me in the right direction. I'm very new to linux.

---

### Post by IYII3r41n on 2013-10-04
I just tried sudo pm-hibernate. It worked like a charm. Same thing with sudo pm-suspend. However when I click the button, it wakes to a freeze. I might just bail on suspend and change settings in dconf to hibernate instead of suspend. Being a geek, i would still like to try and fix the issue.

---

