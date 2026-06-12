---
title: "Screen Resolution Issues"
date: 2007-12-07
forum: General Help
---

### Post by AHelter on 2007-12-07
I see that there are a couple threads on Screen Resolution Issues, but I don't see any that match my issue and was hoping the community could help an aspiring Linux User.

So I have a slightly old computer that I has hard drive issues and can only successful boot on Linux.  I used to use a live CD, but decided to go full linux and install Ubuntu.  But my issue is that whether it ran on the live CD or now on the install, the screen resolution is stuck at 640x480 as my only option, and 60Hz as my only refresh rate option.  It is driving my wife and I insane, and the only way I can convince her not to go back to Monopolysoft is if I can get this issue resolved.

It is a generic POS desktop (Fintec) with a sony LCD monitor SDM-M51.  Usually I know more about the machines I use, but there is no documentation on my wife's old desktop and I'm not used to the Ubuntu display of hardware information.

Can anyone help me get my resolution to something reasonable so I am not only seeing 1/8 of any browser?  If you need any more info I will be happy to provide.

Thank you!

PS:  Completely new to trying to interact with my computer on a script level, so "click this, then click that, then type this" would be the best form of guidance until I can poke around in Ubuntu in a more friendly environment than a super zoomed microscopic view mentally allows me to do.

---

### Post by heatpumpcontrol on 2007-12-07
find a suitable refresh rate for your monitor. Maybe you can run it off the CD again and see what the xorg.conf file is using as a refresh rate and monitor settings. Write these down. Reboot normally  and when you log back in do a 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

```
gksudo gedit /etc/X11/xorg.conf
```
Now compare what you had while using the CD in the monitor section and just replace with what you have written down.

---

### Post by AHelter on 2007-12-08
Hi.  Thank you.  When I do that I get the following.

	Monitor		"SDM-M51"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
EndSection

It is no different from my CD though, they both provide the same default resolution.  And even though in the script it lists 720x400 & 640x400, neither of those options really exist.

If I replace the 640x480 portion of the script wherever 640x480 is listed to something like, 1280×1024, will it change my default resolution to 1280x1024?

Thanks!

---

### Post by CatKiller on 2007-12-08
> **AHelter said:**
> It is a generic POS desktop (Fintec) with a sony LCD monitor SDM-M51.

Use ```
gksudo gedit /etc/X11/xorg.conf
``` after making a backup to add the following information to your Monitor section

```
     HorizSync     28-64
     VertRefresh     48-75
``` (values taken from the specs on Sony's site)

And put "1024x768" and "800x600" into the Mode lines of the Screen section.

It's also possible that you'll need to use a more specific driver for your graphics card. ```
lspci | grep VGA
``` should tell you more information about what the graphics card thinks it is.

---

### Post by Victormd on 2007-12-08
Hi. I'm totally new to the ubuntu environment as well. I have a similar issue with my monitor refresh rate. A bit of background... I know little to nothing about linux/ubuntu settings via command line and am afraid to mess around with my xorg.conf without help (don't want to keep reinstalling ubuntu)

I have a ViewSonic VA1912wb and the resolution is set to 1440x900
My first Ubuntu install selected the proper resolution and refresh rate = 60Hz

Playing around, my machine crashed and I figured it would be easier to format and reinstall Ubuntu... well, now my resolution is still 1440x900 but the refresh rate = 70Hz and every time I restart my computer the graphical interface does not enter, I get a screen with a few lines and that's it. My work around is to go to the command line and CTRL+ALT+DEL from there gets me into the graphical interface.

I think the problem is the refresh rate and I can't change it. My only options under SYSTEM>PREFERENCES>SCREEN RESOLUTION are 70 and 72Hz and I know that my monitor doesn't like that.

My video card is a nVIDIA FX5200 and the drivers are correctly installed (a proof is that I have compiz-fusion up and running).

Please help!
Thanks

---

### Post by CatKiller on 2007-12-08
> **Victormd said:**
> My video card is a nVIDIA FX5200 and the drivers are correctly installed (a proof is that I have compiz-fusion up and running).

Compiz-Fusion (and Compiz and Beryl, for that matter) incorrectly report the screen refresh rate. I have no idea why. For example, mine is saying that it's doing 50Hz even though the monitor knows that it's doing 60.

I suspect that your refresh rate is still 60 and it's something else that's causing your problems when you first start up. I don't know what that would be, though.

---

### Post by Victormd on 2007-12-09
I don't know what the problem was but I played around a bit with my xorg.conf file and in the end, changed several things so I'm not sure which one did the trick... but thanks for the heads up on the refresh rate issue from compiz-fusion. However, on my previous install, I had compiz-fusion installed and the refresh rate was reported correctly... but I'll keep looking.

Thanks!

---

### Post by Victormd on 2007-12-28
Just an update.
I've clean installed Ubuntu on my AMD64 and none of the refresh rate issues occured!
Go figure...

---

