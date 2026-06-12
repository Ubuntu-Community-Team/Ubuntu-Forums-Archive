---
title: "[SOLVED] Xorg problems after kernel update"
date: 2007-12-20
forum: General Help
---

### Post by Sef on 2007-12-20
I have an NVidia 8600 GT and a Samsung Monitor.   After upgrading the kernel, I now get this.   How exactly can I get NVidia and my monitor back to how it was with the old default (1024x768.)   

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection

---

### Post by overdrank on 2007-12-20
HI and Sef when I have any Failsafe in my xorg I usually have to reconfigure my xorg to get it working properly. I do not have that particular model graphics card but have you tried Envy.

---

### Post by PmDematagoda on 2007-12-20
But if you already have the nvidia-glx packages then they could conflict with the driver installed by Envy, so remove those packages(If you do have them) before using Envy.

---

### Post by Sef on 2007-12-21
> HI and Sef when I have any Failsafe in my xorg I usually have to reconfigure my xorg to get it working properly.

What's the best way to reconfigure xorg?  I would like learn how to do it instead of simply installing a script.

---

### Post by overdrank on 2007-12-21
> **Sef said:**
> What's the best way to reconfigure xorg?  I would like learn how to do it instead of simply installing a script.

Well I would start with backing up the xorg
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then you can use the command ```
sudo dpkg-reconfigure xserver-xorg
``` and then answer the question. Hopefully this will let you configure your graphics.

---

### Post by Sef on 2007-12-21
Overdrank:

Thank you very much.  It worked!  :)

I even got a resolution I did not know that I could do.  (1280x1024.  My old was 1280x768.)

---

### Post by overdrank on 2007-12-21
> **Sef said:**
> Overdrank:

Thank you very much.  It worked!  :)

I even got a resolution I did not know that I could do.  (1280x1024.  My old was 1280x768.)

Great glad to hear. :guitar:

---

