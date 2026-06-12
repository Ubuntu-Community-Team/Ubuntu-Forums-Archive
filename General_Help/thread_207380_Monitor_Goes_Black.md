---
title: "Monitor Goes Black"
date: 2006-07-01
forum: General Help
---

### Post by TinyDoctorTIm on 2006-07-01
All goes well in the Ubuntu 6.06 install, but when it's time to log into the GUI my monitor goes completely black, as if it were receiving no signal at all from the PC. It's an old monitor, and I suspect that the PC is sending it a signal at a resolution or refresh rate that it can't cope with. I have read on the forums that Ubuntu defaults to 1024 x 768 pixels; is it possible to make some adjustments to get a lower resolution, like 800 x 600? Please keep in mind that I can't see the GUI at all, I'll need to work at the command line.

Thanks,

Tim.

---

### Post by scxtt on 2006-07-01
boot into recovery mode and check out your /etc/X11/xorg.conf, see what resolution/refresh rate it's defaulting to ...

---

### Post by TinyDoctorTIm on 2006-07-02
The file /etc/X11/xorg.conf makes reference to a 1280 x 1024 resolution, which my monitor cannot support. Like I said, it's old. Can I edit this file so the system defaults to 1024 x 768? That's a resolution that worked just fine in Ubuntu 5.04.

---

### Post by musther on 2006-07-02
Yes you can, you'll need to edit it on the command line, so use a command line editor like vi.

You should be able to do it like this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo vi /etc/X11/xorg.conf
```

Then move down until you see a section like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor		"LM722"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

You need to remove all the bits that say "1280x1024" so it will look like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor		"LM722"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Then save it and reboot into normal mode, all should be well.

If you make a mess of xorg.conf, the first line I gave you has backed it up to /etc/X11/xorg.conf.old

To learn how to use vi, type:

```
man vi
```

Into google.  If you need any more help, or can't figure out vi, just let us know.

---

### Post by TinyDoctorTIm on 2006-07-02
Thanks, Musther. I was reading a help document about editing xorg.conf just about at the same time that you were posting your response. You got to the point a lot more quickly, so I followed your instructions instead.

I am now the proud owner of a (working) PC with Ubuntu 6.06 on it. It's going to be nice to get rid of the creaky Linspire distro I've been using. It was also nice to discover that I still remember the basics of editing a doc in vi. Every once in a while you need to be brought face-to-face with an unforgiving command prompt, just to be sure you still know what to do about it! :grin:

---

### Post by musther on 2006-07-02
Glad I could help.

---

