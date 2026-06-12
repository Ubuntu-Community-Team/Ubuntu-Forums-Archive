---
title: "Screen 'Refreshes' Often then not all Elements are Reloaded"
date: 2008-05-25
forum: General Help
---

### Post by wersdaluv on 2008-05-25
I edited the screen section
of my xorg.conf because my GDM's screen resolution is too big. 

Now it is ```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
	EndSubSection
```

I forgot how it was before.

Now, my screen often 'refreshes'. By that, I mean, it turns white then some 'elements' on the screen are refreshed immediately like some parts of the gnome panel. In order to refresh other 'elements', I have to hover my mouse over them, switch to another virtual desktop, etc.

How do I fix this? 

I attached screenshots :)

---

### Post by diablo75 on 2008-05-25
```
dpkg-reconfigure xserver-xorg
```

---

