---
title: "1680*1050 resolution not show up on monitor correctly"
date: 2007-10-19
forum: General Help
---

### Post by andrewabc on 2007-10-19
I have Acer E6300 Intel dual core 1 gb ram.
Intel 965g x3000 video card
I have LG 20.1 inch LG 204WT

Using the i386 live cd 7.10 when it boots up the 1680*1050 resolution it correctly detects does not show up on monitor correctly. It also correctly recognizes my montior. It looks like
[http://img208.imageshack.us/img208/2554/ubuntuscreenlz2.jpg](http://img208.imageshack.us/img208/2554/ubuntuscreenlz2.jpg)

I try every LG monitor setting available that has 1680*1050 but none of them work. The same thing happens in xubuntu as well.

Bug report I made which includes xorg:
[https://bugs.launchpad.net/ubuntu/+bug/154412](https://bugs.launchpad.net/ubuntu/+bug/154412)

It correctly identifies my video card, monitor and resolution but it doesn't show up on the screen correctly??

---

### Post by Frak on 2007-10-20
```
sudo dpkg-reconfigure xserver-xorg
```
And answer the questions.

---

### Post by andrewabc on 2007-10-21
Thank you for the reply.
I did what you said and picked all the default options (which appeared to be correct). It recognized the correct resolution (1680*1050). Once I was done the only place it changed to that resolution was the login screen. Ubuntu desktop changed resolution to (screen and graphics preferences)
custom 1 resolution:1280*960 60hz

My best guess is maybe the vertical and horizontal rates are wrong (default values for monitor) and maybe need to be changed to have the 1680*1050 resolution fit correctly on my monitor.
Actually according to [LG website](http://www.lge.com/products/model/detail/l204wt.jhtml) I know the horizontal frequency is different than the one in the setting thing you told me to do. Will change to the values on LG website. Actually the only difference between website and ubuntu is in horizontal in ubuntu is 28 and website is 30.
Changing the horizontal rate makes no difference.

---

### Post by jkerr on 2007-10-21
I have the same problem with my LG L204WT with a nVidia 6600 GT video card.  Ran through Frak's suggestion as well, 1680x1050 is a selectable resolution but when selected, it just gives an improper resolution (actually the same as 1280x1024 but with scrolling) and has some graphics glitches.  I had it working properly before upgrading to 7.10.

Thanks

---

### Post by andrewabc on 2007-10-21
> **jkerr said:**
> I have the same problem with my LG L204WT with a nVidia 6600 GT video card.  Ran through Frak's suggestion as well, 1680x1050 is a selectable resolution but when selected, it just gives an improper resolution (actually the same as 1280x1024 but with scrolling) and has some graphics glitches.  I had it working properly before upgrading to 7.10.

Thanks
Maybe you could run a feisty live cd and copy the xorg or look at settings to see what it was using and maybe we can manually input the info to use for Gutsy?

---

### Post by jkerr on 2007-10-21
Well, I got it working, but I'm not exactly sure how...  

I read in another post that it could be using /etc/X11/xorg.conf.failsafe, which could account for why my changes to xorg.conf didn't seem to do anything.  So I replaced the failsafe one with the regular file and restarted X - it came up in safe mode where I could pick monitor and video driver again.  So I played around with that for a while, and noticed that when I picked a generic LCD 1680x1050 display with widescreen checked and nv for the video driver and logged out for changes to take effect, they didn't seem to be saved - when I got back in they were back to plug n play monitor and default video driver.  I repeated this process about 5 more times, trying to get it to save and hit upon some magical combination that saved these choices - now I've got it in 1680x1050 and everything's great.... Unfortunately I can't be more specific on what I did or how I got here...

Good luck!

---

### Post by andrewabc on 2007-10-21
I know what you mean.
Is it normal to have 22 xorg.conf in X11 folder?
xorg.conf
xorg.conf.1
xorg.conf.2
etc etc.
Then I have a couple xorg.conf.20071021122113 files which are backups I think.

I do not have a xorg.conf.failsafe in X11 folder

EDIT:
I just tried changing resolution again, and I now notice I am up to xorg.conf.24 (was only up to xorg.conf.22 before).
What's with all these new xorgs being created? Backups? Doesn't make sense to create a new one every time I change resolution. Maybe this is what is wrong?

Maybe something in 
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
is wrong? what are your numbers jkerr in xorg.conf?

Also what is
> SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1440x900@60"	"1600x1024@60"	"1280x800@60"	"1680x1050@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
the "Virtual	1680	1050" part for? I'm currently running at 1440*900.

---

### Post by Light- on 2007-10-21
I had this problem with my LCD too, heres how I got it working:

System>Administration>Screens ans Graphics

set your screen model to Generic LCD Panel 1680x1050

make sure the "widescreen" box is checked otherwise for some stupid reason 1680x1050 wont show up in the resolution box

click "ok" and select 1680x1050 in the resolution dropdown box

click "ok" and restart X (ctrl+alt+backspace)

hopefully this works for you

---

### Post by andrewabc on 2007-10-21
> **Light- said:**
> I had this problem with my LCD too, heres how I got it working:

System>Administration>Screens ans Graphics

set your screen model to Generic LCD Panel 1680x1050

make sure the "widescreen" box is checked otherwise for some stupid reason 1680x1050 wont show up in the resolution box

click "ok" and select 1680x1050 in the resolution dropdown box

click "ok" and restart X (ctrl+alt+backspace)

hopefully this works for you
I've tried that several times. But it keeps reverting back to a different resolution (currently 1280*960).

Oddly when I manually edit xorg.conf and only have "1680x1050@60" listed. It still chooses another resolution.
Although when I do actually get my screen to show 1680*1050 it looks like the picture in my first post where it only takes up 2/3 of screen.

---

### Post by rebegin on 2008-01-14
hey, i've found a working modeline while using the DVI socket (though i don't know if there's a difference) so here's my modeline which is working with the latest ati drivers too!!! (8.443)

```

Section "Monitor"
	Identifier	"L204WT"
	Option		"DPMS"
	Modeline "1680x1050@55" 140.00 1680 1712 2240 2272 1050 1071 1081 1103
	Modeline "1680x1050@61" 146.25 1680 1772 1948 2204 1050 1053 1059 1089 +hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"L204WT"
	Defaultdepth	24
	SubSection "Display"
		Modes	"1680x1050@61"	"1680x1050@55"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

```
hope it helps

---

### Post by orb9220 on 2008-01-15
> Also what is
Quote:
SubSection "Display"
Depth 24
Virtual 1680 1050
Modes "1440x900@60" "1600x1024@60" "1280x800@60" "1680x1050@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
EndSubSection
the "Virtual 1680 1050" part for? I'm currently running at 1440*900.

Yep I noticed this two the one monitor was working find then I enabled the nvidia restricted. Then selected admin>screens and graphics.  enabled 2nd monitor which was in list a Compaq presario. Had both set to 1280x1024 log-off.

When I logged back in I got to rolling scrolling windows. of 1400x1050. Why in the hell is  it doing this?

I got around this by changing both virtuals from 1400x1050 to 1280x1024 that worked after logging back in. 

Need to look into further on why the hell they want to automatically give everybody scrolling virtual windows when nobody I know out of hundreds use them.

---

