---
title: "Ubuntu 21.04 boots into 640x480 screen - can't change"
date: 2021-09-06
forum: General Help
---

### Post by criageek on 2021-09-06
I recently had a hard disk failure.  After picking up a new hard disk, I installed a fresh copy of Ubuntu 21.04, restored all my data from backups, and everything was working well.  After a reboot, my system booted into a 640x480 screen and I am unable to change it.  Display settings says "Unknown display".  I have a 4k TV I use as a monitor using the HDMI input.  If I boot using a live USB the display is full resolution, so I know the hardware is good.

I've tried these commands:

sudo dpkg-reconfigure xserver-xorg
sudo X -configure

Neither makes a difference.  What can I try?  I've been using Ubuntu since 2006 but really know very little about X11.

Thanks for any help!

Rich

---

