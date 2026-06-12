---
title: "Is there a way to simulate a USB device being unplugged and replugged in on linux?"
date: 2015-01-11
forum: General Help
---

### Post by dorlow on 2015-01-11
I'm trying to get Fitbit to sync on my Linux workstation using the USB dongle.  I have it working and setup in crontab to run every few minutes.  But the sync seems to work once and then to sync again, I need to unplug and replug in the dongle.  I know most things on linux are config files (if not all) and restarting of a service.  So, I was thinking maybe there's a file I could delete or move, then cycle a service, then put the file back and cycle the service and it would be the same to the PC as unplugging the dongle and plugging it back in.  Then I'll just create a script to simulate unplug and replug it in and run the service to sync the tracker.

---

### Post by efflandt on 2015-01-11
There used to be commands for ejecting/refreshing pc cards like they were just plugged in. But now all of that is handled by udev. I don't know specifics, but maybe a place to start looking for a way to do that is **man udevadm**

---

