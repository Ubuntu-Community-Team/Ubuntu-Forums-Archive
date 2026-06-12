---
title: "ATI Radeon X1650 Pro Help"
date: 2007-11-02
forum: General Help
---

### Post by Shyper on 2007-11-02
Hey, I just installed an ATI Radeon X1650 Pro graphics card; an nVidia card was not available for both the graphics power I wanted and the low-profile slot I had. Anyway, right now I'm stuck with a pretty crappy 800x600 resolution. My Restricted Drivers Manager says the ATI accelerated graphics driver is enabled, but not in use. Can anyone help me? Thanks a lot.

---

### Post by Shyper on 2007-11-02
Bump?

---

### Post by Shyper on 2007-11-02
Bump again? Sorry, I'm really stuck on this, and I'm running Vista until I can get this fixed.

---

### Post by burakerenn on 2007-11-22
I've got the same issue though. I tried to install official ati drivers from his website, but still xserver-xorg is not recognizing my x1650 and ati catalyst control center says "no ati graphics driver installed or the ati driver is not functioning properly". 

I think you can manage your problem with editing /etc/X11/xorg.conf by changing the line starts with Modes like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"PHILIPS 107E"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
                Modes "1024x768"
	EndSubSection
```

As you see I'm trying to stick my resolution to 1024x768 with Modes... line. 

But I'm still looking for a better solution for myself too. I'll let you know if i can figure out.. :(

---

### Post by ropsta on 2007-11-22
[http://ubuntuforums.org/showthread.php?t=611492](http://ubuntuforums.org/showthread.php?t=611492)

^Where I went^

Got Beryl/Compiz Working with x1650pro

This link is only half.  There is a link to the other half on the page though.

---

### Post by kshane on 2007-11-22
> **burakerenn said:**
> I've got the same issue though. I tried to install official ati drivers from his website, but still xserver-xorg is not recognizing my x1650 and ati catalyst control center says "no ati graphics driver installed or the ati driver is not functioning properly". 

I think you can manage your problem with editing /etc/X11/xorg.conf by changing the line starts with Modes like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"PHILIPS 107E"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
                Modes "1024x768"
	EndSubSection
```

As you see I'm trying to stick my resolution to 1024x768 with Modes... line. 

But I'm still looking for a better solution for myself too. I'll let you know if i can figure out.. :(

I have the same card.  I have no trouble with running at 1280x1024.  How did you install?  I normally use Envy to install, but i just now installed the newest release (from yesterday) and it's doing fine so far.

I would suggest using Envy to install the ATI driver, if you're having problems with it.

Kevin

---

