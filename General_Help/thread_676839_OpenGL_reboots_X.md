---
title: "OpenGL reboots X"
date: 2008-01-24
forum: General Help
---

### Post by Mufloon on 2008-01-24
Hi,

I'm having an issue as mentioned in the title, and I've seen multiple people mentioning about this (over here, and other forums). OpenGL reboots the desktop environment whenever it is run, *except when in fullscreen mode*. Meaning, when I try to select a different screensaver, and the preview is about to be shown in the window, X reboots. However, when the screensaver activates (I currently have a OpenGL screensaver set) it does *not* reboot. The same issue pops up when I'm trying to run some Ogre sample applications: as soon as the apps load in a windowed environment: reboot. When running them fullscreen, I do not see anything except of a part of my desktop zoomed in (due to the resolution change). glxGears also fails by the way.

My laptop (Acer Aspire 7720Z) uses Intel Integrated graphics, and I didn't find any new drivers for that. I've reinstalled the current one, but to no avail. System logging does not directly provide any interesting results in this direction.

Does anyone have any idea what may cause this?

Thanks in advance!

---

### Post by kuja on 2008-01-24
> **Mufloon said:**
> Does anyone have any idea what may cause this?
My bet is on the video drivers.

If you're using the latest version of Ubuntu did it work with older versions? Or, if you're not, have you tried Gutsy to see if it resolves the problem?

Might be worth a shot at any rate.

---

### Post by Mufloon on 2008-01-25
Yeah, my best guess is that it has something to do with those drivers as well. I'm currently running Gutsy (so, 7.10) which I installed when I received the laptop. Therefore I have no comparison for older versions since they have never been installed. And I'm a bit reluctant to install an older version since it is my "active" pc and I had quite some work on installing the wireless drivers et al.

Isn't there a possibility to update only the video drivers? Because I can't find any option or site for that. Or remove the driver, reinstall... something like that?

---

### Post by kuja on 2008-01-26
Which intel gpu in particular was it? What driver are you having X use? (probably i810 or intel)

---

### Post by Mufloon on 2008-01-28
The laptop has it listed as "Intel Graphics Media Accelerator X3100", and it's using the i810 drivers. If I recall correctly, there are two different driver sets for these cards in the repositories, but they didn't offer any different result. As a matter of fact, I don't see any difference in having any of them installed (if installed at all)... :(

---

### Post by kuja on 2008-01-28
Installing alone isn't enough, you also need to be using them. I'm assuming this is what we need to do, so give it a shot:

```
sudo apt-get remove xserver-xorg-video-i810
sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg
```

The most important part is selecting the video driver here, and you need to select "intel".

I've also attached a sample xorg.conf for you to look at should you need to.

---

### Post by Mufloon on 2008-01-28
Ok, thanks! I'll try it when I get home (about 5 hours from now), but one quick remark: you said you attached a sample xorg.conf... but I'm either looking at the wrong place or you forgot to attach it :).

---

### Post by kuja on 2008-01-28
Oh ... that's entirely possible, likely even.

---

### Post by Mufloon on 2008-01-30
:( Didn't work... might it make a difference if I only have a single screen mode listed? Your xorg.conf has the following...

```
	SubSection "Display"
		Modes		"1440x900" "1024x768" "800x600"
	EndSubSection
```

... while mine only lists 1440x900. Next to that, the conf-file seems roughly identical. Dunno if OpenGL defaults to a certain resolution in the screensaver or glxGears demo, and when it isn't listed, crashes? (I'm at work now, so I can't test it, just thinking aloud.) Came to me because when the screensaver kicks in - fullscreen - it does not crash. Can the OpenGL supported resolutions be dependent on the xorg.conf display modes? Because the 3D apps I'm building default to a 640x480 resolution, which isn't in the list... :-k

---

### Post by Mufloon on 2008-01-31
Nope, negative. I'm out of ideas...

---

