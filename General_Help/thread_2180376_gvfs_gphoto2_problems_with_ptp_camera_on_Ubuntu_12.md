---
title: "gvfs gphoto2 problems with ptp camera on Ubuntu 12.04"
date: 2013-10-12
forum: General Help
---

### Post by gnosel on 2013-10-12
Ubuntu 12.04 32-bit with gvfs 1.12.1-0 and gphoto2 2.4.11 connects to my Canon 700D (only PTP, no MSC mode) and opens a folder like "gphoto2 mount on USB[001,001]" and seems to be mounted on ~/.gvfs/

1. I can download photos from that folder but I can't upload/create a file in this folder. Any idea why I can't do this? Is there a special setting for this?

2. When I browse or copy the files in the gvfs/gphoto2 folder the file's time stamp is two hours. If camera and PC have 9:00 then the image file shows 11:00. If I take the camera SD card into the card reader the file shows the correct time, so the issue seems to be related to gvfs-gphoto2. PC and camera are set to the time zone GMT+1 (Paris) +DST, so 2 hours in total. Is there a setting to change this behaviour?

I don't need gphoto2, so if there is a way to mount a ptp camera as a normal usb device I would be happy as well.

Thanks!

---

