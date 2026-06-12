---
title: "Screen resolution help."
date: 2007-04-26
forum: General Help
---

### Post by EvenStevens on 2007-04-26
For reasons that I can't be bothered explaining, I reinstalled Ubuntu Feisty Fawn on my laptop. Setup went fine as it did first time round...but my screen res dropped down to 1024x768.
Now, this happened first time round but I read up on the 915resolution hack and applied it...and it worked fine. No hassle.

This time, however...it just doesn't work. I've followed these instructions to a tee - [http://knowledge76.com/index.php/Resolution_1440x900_with_Intel_945GM](http://knowledge76.com/index.php/Resolution_1440x900_with_Intel_945GM)

Obviously, using the newer version of 915res.

But...to no avail!
It still starts up in 1024 768 and that's the maximum it's sticking at :|

Here's my xorg.conf file.

> Section "Monitor" 
	Identifier	"Generic Monitor" 
	Option		"DPMS" 
	HorizSync	28-72 
	VertRefresh	43-60 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"Generic Video Card" 
	Monitor		"Generic Monitor" 
	DefaultDepth	24 
	SubSection "Display" 
		Depth		1 
		Modes		"1440x900" 
	EndSubSection 
	SubSection "Display" 
		Depth		4 
		Modes		"1440x900" 
	EndSubSection 
	SubSection "Display" 
		Depth		8 
		Modes		"1440x900" 
	EndSubSection 
	SubSection "Display" 
		Depth		15 
		Modes		"1440x900" 
	EndSubSection 
	SubSection "Display" 
		Depth		16 
		Modes		"1440x900" 
	EndSubSection 
	SubSection "Display" 
		Depth		24 
		Modes		"1440x900" 
	EndSubSection 
EndSection

I remember last time I looked at this file, it was set to 1440x900 everywhere and when I ran 915, it sorted it straight out.
Now...doesn't seem to be the case.

I'm using a Dell Inspiron 640m with** Intel 945GM** graphics.

---

### Post by sevencapitalsins on 2007-04-26
You may want to uninstall the previous 915resolution (i gave a quick look at your link) and install the ubuntu-provided one:

```
sudo apt-get installl 915resolution
```

It is strange, but sometimes just sticking to ubuntu's packages works fine.

Bye,
Luca

---

