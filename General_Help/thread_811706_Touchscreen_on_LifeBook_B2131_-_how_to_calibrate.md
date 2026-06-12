---
title: "Touchscreen on LifeBook B2131 - how to calibrate?"
date: 2008-05-29
forum: General Help
---

### Post by superwormy on 2008-05-29
I'm trying to calibrate the touchscreen on a Fujitsu Lifebook B2131 laptop... and I'm getting strange errors. Can anyone help me with this? 

I've added the Option Calibrate 1 line to my /etc/X11/xorg.conf and I run the /usr/lib/xf86-input-evtouch/ calibrate.sh script like this:

sudo calibrate.sh

First, I get an error that ReportingMode Raw is not valid, so I commented that out. 

Then, I get an error that looks like this:

(EE) Touchscreen: Unable to grab device (Inappropriate ioctl for device).
XReadBitmapFile - could not open file '/empty_cursor.xbm'.
X Error of failed request: BadPixmap (invalid Pixmap parameter)
... etc. etc. etc. 


Ideas?

---

### Post by mu3en on 2008-08-18
I have the same error in Kubuntu Hardy. Any feedback on the "(EE) Touchscreen: Unable to grab device (Inappropriate ioctl for device)."?

I have calibration commented out in xorg.conf and official repo install of xserver.xorg.input.evtouch

Can anyone confirm that evtouch must be set to /dev/input/touchscreen in the xorg.conf as suggested?

---

