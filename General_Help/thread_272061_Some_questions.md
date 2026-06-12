---
title: "Some questions"
date: 2006-10-05
forum: General Help
---

### Post by elixir4001 on 2006-10-05
Hello everyone! I just installed ubuntu for the first time on my Gateway 400VTX laptop a couple days ago. So far i am really impressed...never having used linux before:cool: . However one problem i see which seems like everyone has...and ive looked and tried pretty much everything. But my stupid screen resolution will just not change. (yes i know another resolution question) If anyone has some insight on how to help me tell me and ill tell you if ive tried it. graphics card: Intel Corporation 82852/855GM Integrated Graphics Device

also how do i turn off the annoying tapping of the mousepad being seen as a double click?
thanks all!!
-alex

---

### Post by Jagot on 2006-10-05
I believe you need 915resolution, which is in the universe repository:

```
sudo aptitude update
sudo aptitude install 915resolution
```

With my Dell, it set the resolution automatically after installing - just needed to restart.  If it doesn't for you, then follow the instructions here:

[http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html)

---

### Post by elixir4001 on 2006-10-06
well that sucks, didnt work. I had 915 already but i tried those steps and it didnt work:( anything else?

---

### Post by Jagot on 2006-10-06
Have you tried editing your xorg.conf manually?

---

### Post by elixir4001 on 2006-10-06
yea, i have and with no avail, unless it is setup wrong this is how it looks:
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Gateway 400VTX"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Gateway 400VTX"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by elixir4001 on 2006-10-09
ok ive been trying (mostly with 915resolution as i believe thats what i need) and i still can not get it](*,) . so if anyone can lend some assistance i would love you forver:mrgreen:

---

### Post by elixir4001 on 2006-10-11
arite well ive still been trying everything here guys, posting on other forums too. Is there no concrete fix for this problem?
I dont think i stated this before, but i am trying to get 1024x768 out of my monitor (which i know can display) but only 640x400 and 800x600 show up

---

