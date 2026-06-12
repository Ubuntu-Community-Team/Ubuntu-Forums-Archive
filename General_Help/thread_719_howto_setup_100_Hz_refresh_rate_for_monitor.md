---
title: "howto setup 100 Hz refresh rate for monitor?"
date: 2004-10-15
forum: General Help
---

### Post by tanari on 2004-10-15
now i have 1280-1024@85Hz, how to setup 100hz?

My XF86Config-4 file:
```
Section &quot;Monitor&quot;
	Identifier	&quot;P95f+&quot;
	HorizSync	30-110
	VertRefresh	50-160
	Option		&quot;DPMS&quot;
EndSection

Section &quot;Screen&quot;
	Identifier	&quot;Default Screen&quot;
	Device		&quot;ATI Technologies, Inc. Radeon 7200 &#40;R100 QD&#41;&quot;
	Monitor		&quot;P95f+&quot;
	DefaultDepth	24
	SubSection &quot;Display&quot;
		Depth		1
		Modes		&quot;1920x1440&quot; &quot;1792x1344&quot; &quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1024x768&quot; &quot;832x624&quot; &quot;800x600&quot; &quot;720x400&quot; &quot;640x480&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		4
		Modes		&quot;1920x1440&quot; &quot;1792x1344&quot; &quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1024x768&quot; &quot;832x624&quot; &quot;800x600&quot; &quot;720x400&quot; &quot;640x480&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		8
		Modes		&quot;1920x1440&quot; &quot;1792x1344&quot; &quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1024x768&quot; &quot;832x624&quot; &quot;800x600&quot; &quot;720x400&quot; &quot;640x480&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		15
		Modes		&quot;1920x1440&quot; &quot;1792x1344&quot; &quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1024x768&quot; &quot;832x624&quot; &quot;800x600&quot; &quot;720x400&quot; &quot;640x480&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		16
		Modes		&quot;1920x1440&quot; &quot;1792x1344&quot; &quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1024x768&quot; &quot;832x624&quot; &quot;800x600&quot; &quot;720x400&quot; &quot;640x480&quot;
	EndSubSection
	SubSection &quot;Display&quot;
		Depth		24
		Modes		&quot;1920x1440&quot; &quot;1792x1344&quot; &quot;1600x1200&quot; &quot;1280x1024&quot; &quot;1024x768&quot; &quot;832x624&quot; &quot;800x600&quot; &quot;720x400&quot; &quot;640x480&quot;
	EndSubSection
EndSection
```

---

### Post by HungSquirrel on 2004-10-15
To guarantee a 100Hz refresh rate you will have to add a 'Modeline' to your config. There are some [sites](http://www.google.com/search?q=modeline+generator&amp;sourceid=firefox&amp;start=0&amp;start=0&amp;ie=utf-8&amp;oe=utf-8) out there that can help you figure out the modeline you need.

I don't bother with modelines because I am happy with the default refresh rates.  As long as you specify your monitor's specific horizontal and vertical frequencies, X tends to give a nice default refresh rate in my experience.

---

### Post by tanari on 2004-10-15
I find a few sites through google, added 'a modeline' to XF 86Config-4, after that x server failed to start, so I reinstalled ubuntu :(.

---

### Post by Perfect Storm on 2004-10-15
Check here: [http://ubuntuforums.org/viewtopic.php?t=558](http://ubuntuforums.org/viewtopic.php?t=558)
I had similiar problem

---

### Post by HungSquirrel on 2004-10-15
[quote=tanari]I find a few sites through google, added 'a modeline' to XF 86Config-4, after that x server failed to start, so I reinstalled ubuntu :(.[/quote]
You don't need to reinstall when you have a problem.  When you boot, press Esc to bring up the GRUB menu, then choose the failsafe option (I forgot the exact name).  Then you can login as root (your password will probably be blank, so just hit Enter.)  Then you can use a console text editor to fix the problem, e.g. *nano /etc/X11/XF86Config-4* .  Add a "#" at the beginning of the modeline to comment it out.  Ctrl+x to quit and save.  Then type *reboot* to reboot.

---

### Post by daniels on 2004-10-16
What you want is to have the configuration file as it first was, but then delete the HorizSync and VertSync lines.  This should give you enough; if not -- and only if you're positive your monitor's capable of pulling 100Hz -- grab some ModeLines from Google.

---

### Post by FLeiXiuS on 2004-10-16
I agree modelines should do it for you, google is your friend dont be afraid to use it :-).

---

### Post by tanari on 2004-10-18
nothing help :(
after adding modeline, X don't start

I deleted the HorizSync and VertSync lines, but nothing changes, i can't setup more than 85 Hz

---

### Post by HungSquirrel on 2004-10-18
Not to be rude, but what's wrong with 85Hz?  I'm happy with 75!   :?

---

### Post by tanari on 2004-10-19
my monitor can view 100 Hz, it is better than 85 :)

---

### Post by Rancoras on 2004-10-19
You can see the diference between 85 and 100?  You have better eyes than me.

---

### Post by tanari on 2004-10-19
in 1024x768 can't, but in 1280x1024 at white background can

---

### Post by c0ld on 2007-01-06
hi all, im new to this ubuntu, but if i understand things right, this is just a kind of linux operation system right?

I dont have this on my laptop, im just curious, if its possible to pump up the Hz in windows on your laptop, or 75 hz crt monitor?

if there is any config file from windows where i configure this

---

### Post by Wim Sturkenboom on 2007-01-06
If you can see the difference between 85Hz and 100Hz, it is better. If you don't see the difference, you're probably shortening the lifespan of your monitor.

X errors are written to /var/log/Xorg.0.log. So have a look for errors there (lines starting with EE).

You don't necessarily need a modeline for this. Try to add the bold line below to the *device* section your config and see if it works:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    **Option         "UseEdidFreqs" "false"**
EndSection

```

---

### Post by Wim Sturkenboom on 2007-01-06
> **c0ld said:**
> hi all, im new to this ubuntu, but if i understand things right, this is just a kind of linux operation system right?

I dont have this on my laptop, im just curious, if its possible to pump up the Hz in windows on your laptop, or 75 hz crt monitor?

if there is any config file from windows where i configure this

Your monitor is either recognized by Windows or came with a disk with the configuration.
Warning: don't exceed the specification of the monitor

---

