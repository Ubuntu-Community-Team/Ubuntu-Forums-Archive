---
title: "Power outage last night. Now system only boots to Emergency mode"
date: 2019-06-06
forum: General Help
---

### Post by lsutiger on 2019-06-06
From the journalctl, here is what is in red:
```
invalid key value pair in file /etc/udev/rues.d/11-android.rules on line 1, starting at character 43("\")
unknown key 'SYSFS[idVendor]' in /etc/udev/rules.d/40-brother-libsane-type1.rules:17
invalid rule '/etc/udev/rules.d/40-brother-libsane-type1.rules:17
systemd[1]modules-load[318]: Failed to insert 'it87':device or resource busy
systemd[1]: Failed to start Load Kernel Modules
```
Here's an odd one. It is looking for a network interface that is not there. The name it is looking for is enp2s5, but the name is enp2s6 - I am sure of this because I edited a conky script two days ago to list this. Here is the red part:
```
Failed to start Raise  network interfaces
```
I booted on a live usb and ran fsck on all file systems and all return clean. Tried the first 3 steps from [this search]("https://www.google.com/search?client=firefox-b-1-d&channel=cus&q=ubuntu+emergency+mode") and so far nothing has worked.

I will continue on, but would love some input on this!

---

