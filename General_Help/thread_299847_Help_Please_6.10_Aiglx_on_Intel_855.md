---
title: "Help Please 6.10 Aiglx on Intel 855"
date: 2006-11-14
forum: General Help
---

### Post by luckylucky on 2006-11-14
Please help...

I am desperately wanting to run aiglx on my laptop with an intel 855 video card.  From my online searching of "how to" info it seems that this is possible, however I can't find a good "how to" that does the trick.  Can anyone please point me to a page that explains how to run aiglx in edgy on an intel 855 please?  Thanks in advance!

---

### Post by GStubbs43 on 2006-11-14
AIGLX is already in Edgy, if you want Beryl, just follow these directions:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
Basically, add ```
deb http://ubuntu.beryl-project.org/ edgy main-edgy
```
to your /etc/apt/sources.list
Then do:
```
sudo aptitude update && sudo aptitude install beryl
```

---

### Post by d3v1ant_0n3 on 2006-11-14
I also had to add the following to my /etc/X11/xorg.conf file :

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
	Option "XAANoOffscreenPixmaps" "true"   *<<<<<I ADDED THAT LINE*
EndSection

Also I added this section:

Section "Extensions"
Option "Composite" "true"
EndSection

---

### Post by luckylucky on 2006-11-14
Damn!!!  This is SWEEEEEEEET STUFF!!!!  Obviously I got it working.  Thanks!  BTW that was easy compared to the work I was prepared to go through to make it work.

BTW, I didn't do any of the stuff mentioned by d3vlant (below).  [COLOR="Red"]**QUESTION:**[/COLOR]  Is this necessary?  Seems to work for me without doing that.


> **d3v1ant_0n3 said:**
> I also had to add the following to my /etc/X11/xorg.conf file :

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
	Option "XAANoOffscreenPixmaps" "true"   *<<<<<I ADDED THAT LINE*
EndSection

Also I added this section:

Section "Extensions"
Option "Composite" "true"
EndSection

---

### Post by GStubbs43 on 2006-11-15
Nah, I don't think it is necessary for *everyone*. Some video cards probably need it though, if it works now, I wouldn't bother with editing your xorg.conf.

---

