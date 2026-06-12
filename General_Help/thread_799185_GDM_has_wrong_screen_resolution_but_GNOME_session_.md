---
title: "GDM has wrong screen resolution but GNOME session doesn't"
date: 2008-05-18
forum: General Help
---

### Post by wersdaluv on 2008-05-18
After installing Hardy, my GDM and GNOME session's screen resolutions were too big that only about 1/4 of the whole view is displayed on my screen. It is odd because the resolutions of my GRUB menu and my Usplash screens were correct.

I manually changed GNOME's resolution to 1024x768 in the screen resolution dialog then my GNOME's resolution was fixed. On the other hand, my GDM screen resolution still is very big. How do I change it?

---

### Post by wersdaluv on 2008-05-19
Bomppp

---

### Post by mc4man on 2008-05-20
many times that caused by the resolution on the virtual line in xorg.conf being to high. If you have mode lines it will sometimes be set to the last one listed. If so change it to something reasonable and correct for your monitor. ex.
```
clipped .....
 modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.17
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 7800 Gs"
	Monitor		"Dell P991"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
```
initially mine was set to 2048  1536

---

### Post by wersdaluv on 2008-05-20
I tried to change mine to 

	SubSection "Display"
		Depth	24
		Virtual	1280	1024

but when I restarted X, I had problems so I had to reconfigure it with Ubuntu's bulletproof X feature. 

After that, I got

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection

but my GDM's resolution is still the samme :(

---

### Post by wersdaluv on 2008-05-21
It worked! I just wasn't able to understand you well. hehe. Thanks! :)

---

### Post by Weidbrewer on 2008-07-11
> **wersdaluv said:**
> It worked! I just wasn't able to understand you well. hehe. Thanks! :)

I must still be missing something, because when I try this, it changes both my login screen and my desktop...so, if I get the login down to a size that fits my monitor, my desk to looks huge (800x600.)

What am I doing wrong?

---

### Post by wersdaluv on 2008-07-11
> **Weidbrewer said:**
> I must still be missing something, because when I try this, it changes both my login screen and my desktop...so, if I get the login down to a size that fits my monitor, my desk to looks huge (800x600.)

What am I doing wrong?

If your GDM screen is fine and your desktop is the only problem, **System** --> **Preferences** --> **Screen Resolution**. :)

---

### Post by wersdaluv on 2008-07-11
> **Weidbrewer said:**
> I must still be missing something, because when I try this, it changes both my login screen and my desktop...so, if I get the login down to a size that fits my monitor, my desk to looks huge (800x600.)

What am I doing wrong?

If your GDM screen is fine and your desktop is the only problem, **System** --> **Preferences** --> **Screen Resolution**. :)

---

### Post by Weidbrewer on 2008-07-11
> **wersdaluv said:**
> If your GDM screen is fine and your desktop is the only problem, **System** --> **Preferences** --> **Screen Resolution**. :)

You'd think that, wouldn't you.


Problem is, when I change the above settings to,say, 800x600...everything above 800x600 disappear from the screen resolution menu.

---

