---
title: "Cannot boot Ubuntu 17.10"
date: 2017-12-01
forum: General Help
---

### Post by Karolina.K on 2017-12-01
Hello

I was using photorec to recover files from an old hard disk, and my system accidentally got full and started acting strange. I tried to launch nautilus in terminal to be able to delete files (it didn't work) so I tried to restart Computer  and now its stuck on the check list and does not boot.

I'm currently writing a paper for university and all my information is there which I need  how can I solve this. 

I add a picture of the place where it stucks hosted by imgur. [https://i.imgur.com/32IO37H.jpg](https://i.imgur.com/32IO37H.jpg)

/Karolina

---

### Post by Karolina.K on 2017-12-01
I want to add that I did boot it with liveusb and deleted maybe 4gb and still it can't boot

---

### Post by Rick St. George on 2017-12-01
Personally I would use the LiveDisk/USB and offload to a thumb drive important docs.  Are you sure the HDD is Ok? May run fsck or e2fsck (see here for instructions [https://askubuntu.com/questions/561865/what-is-the-best-way-to-scan-a-hard-drive-check-health-in-ubuntu](https://askubuntu.com/questions/561865/what-is-the-best-way-to-scan-a-hard-drive-check-health-in-ubuntu)) prior to anything else. You could then try to do a REPAIR (see here for instructions [https://askubuntu.com/questions/726071/repairing-broken-installation-from-live-usb-without-losing-data](https://askubuntu.com/questions/726071/repairing-broken-installation-from-live-usb-without-losing-data)). This will keep all your "data", with your BU of important stuff for safe keeping.

Last option ... Re-Install Ubuntu using your LiveDisk/USB with most current v16.04  LTS. Sounds like something got corrupted (not just full). When doing a Re-Install, be sure to select reformat the HDD, which is more or less automatic upon an install. Then copy your important stuff back to your home folder. Easiest clean method.

If this solves your problem, please select SOLVED, in Thread Tools at top right above your first post.
Hope this helps and best wishes in your studies.

---

### Post by Karolina.K on 2017-12-03
yes I did the last option, and saved the files on usbthumbstick before. Still don't know what happened but its solved :) thanks for the help

---

