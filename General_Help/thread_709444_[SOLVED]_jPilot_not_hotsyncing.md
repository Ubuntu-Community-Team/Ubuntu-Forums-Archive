---
title: "[SOLVED] jPilot not hotsyncing"
date: 2008-02-27
forum: General Help
---

### Post by Bruce M. on 2008-02-27
It was the one thing I was worried about when I installed Ubuntu and I was so happy when I did get it working.

A couple of days ago I tried adding my wife as a user to jPilot, that failed and my T|E2 stopped hotsyncing at that time.
I used the "Mark For Completely Removal" - all things jPilot and reinstalled it.

From [PalmDeviceSetup]("https://help.ubuntu.com/community/PalmDeviceSetup") page I did the following:
```
gksudo gedit /etc/udev/rules.d/10-custom.rules
```
adding:
```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```
Saved and closed gedit and terminal, then
```
gksudo gedit /etc/modules
```
and added "visor" as the bottom line

When I try to hot-sync I get:
```

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

```
On the jPilot page I found this note:
> 
I used these directions and they worked great. but after upgrading to gusty I had problems again. I seems that in gusty there is a udev rule already set up for palm devices that conflicted with this rule above. in the file "60-symlinks.rules" I commented out the rule that was for palm devices and my treo 650 syncs again like before. With the 2 rules together I was getting /dev/pilot becoming symlink to IT'S SELF. if you see some thing like this:

ls -l /dev/pilot lrwxrwxrwx 1 root root 5 2008-01-21 00:10 /dev/pilot -> pilot you might have a similar problem. 

I never saw the above "ls -l ... etc" error.

I found "60-symlinks.rules" file:
```

# This file establishes user-friendly symlinks to devices according to
# Ubuntu policy.  See udev(7) for syntax.
#
# The names of the actual devices themselves must not be set here, but
# in 20-names.rules; the permissions and ownership of those devices
# should be set in 40-permissions.rules.

# Compatibility symlinks for /dev/scd* devices
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*",	SYMLINK+="%k"

# Compatibility symlinks for USB printers
SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  SYMLINK+="usb%k"

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
					SYMLINK+="pilot"

```
But I'm not sure I want to mess with it.

Any ideas out there as to how I can get HotSync working again?
Bruce

EDIT: As an added note /dev/pilot does not exist.

---

### Post by Bruce M. on 2008-02-28
Anyone?

Even if it's a "you could try this..."

---

### Post by Bruce M. on 2008-03-06
Dead thread...
Marking Solved

---

