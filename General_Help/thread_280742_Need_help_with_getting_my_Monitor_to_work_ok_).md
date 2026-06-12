---
title: "Need help with getting my Monitor to work ok :)"
date: 2006-10-19
forum: General Help
---

### Post by thenetduck on 2006-10-19
Hi, 
  I just purchased a 19" widescreen Monitor from Newegg (Hannsg) and I tried to log into my gnome session, but it doesn't let me, the screen goes blank and says (Out of range) I think I need to get the range down to 75 or up to 75. Anywho, does anyone know how I can do this? I like using my gnome session better than KDE and Xubuntu. thanks,
 
The Net Duck

---

### Post by SendDerek on 2006-10-19
This might sound a little redneck-ish, but...

If you still had the old monitor, you could login to gnome, change the resolution settings to something very generic, log out, and then try the new monitor until it works.

lol... like I said, it's redneck-ish.

It would be cool if there was a way to do it from the command line before you logged into the gnome session.

---

### Post by thenetduck on 2006-10-19
Thanks for the Idea, Im ganna try that. Also, do you know how to get a 1440x900 resolution for Gnome?? 

 The Net Duck

---

### Post by SendDerek on 2006-10-19
I believe your hardware has to support it.  That includes both your graphcs card and monitor.

If they do, maybe it's just something as simple as changing the conf file that's in charge of monitor resolution.  (Sorry, I don't know much more than that! lol)

Here's what in my /etc/X11/xorg.conf file:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

See where it has all of the "Display" "1280x800" ?  Maybe you could replace those with the resolution you want.

Also, I know that there is a way to switch between each one of those settings one by one.  It's some kind of keybinding, but I can't remember it.  That would make things easy because then you could experiment will all kinds of different resolutions and not worry about it when you monitor says "out of range", then you could just press some buttons and it would come back!

---

### Post by podunk on 2006-10-19
It's a *real* good idea to back that file up before you change it! :-)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by SendDerek on 2006-10-20
Yeah, What he said ^^^^^^

Good call.

---

### Post by bdb on 2006-10-20
when you edit your xorg.conf back it up as stated earlier.  You will have to restart x everytime for changes to take effect.
```

sudo /etc/X11/gdm stop
sudo /etc/X11/gdm start

```
If it doesn't restart restore your xorg.conf backup file.

---

### Post by thenetduck on 2006-10-20
Hey guys, I just found a much easier way to do this. All I have to do is reconfigure my xorg with this code. 

```

sudo dpkg-reconfigure xserver-xorg

```

Works great. Thanks for the help ;)

 The Net Duck

---

### Post by CatKiller on 2006-10-20
If you want to be really flash, you could try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```since that will only ask you high priority questions about your setup.

---

