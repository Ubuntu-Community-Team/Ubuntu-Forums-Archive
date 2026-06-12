---
title: "Stellarium crashes during start-up"
date: 2007-11-25
forum: General Help
---

### Post by kstella on 2007-11-25
I was impressed by the screenshots of Stellarium, so I installed it today. I can't get past startup, though; it crashes while loading the constellation art.

I'm not in a hurry; it would just be nice to see stars every once in a while when you're living in a light-polluted city. On another note, it's sad to think that we have to resort to computer programs to see the old night sky; coming from a rural province, I thought that was the stuff of sci-fi and that I'd never have to look for stars.

---

### Post by jasmuz on 2007-11-25
Geeky question, do you have an accelerated 3D card?

Try running it from the command line, and post what it spits out.. there we shall find what is wrong.

---

### Post by kstella on 2007-11-27
Okay. This is what I got:

File search path set to:
 1) /home/katrina/.stellarium
 2) /usr/share/stellarium
config file is: /home/katrina/.stellarium/config.ini
Sky language is en_PH.
Application language is en_PH.
Loading Solar System data...(loaded)
Loading star data...
ZoneArray::create(/usr/share/stellarium/stars/default/stars_0_0v0_0.cat): type: 0 major: 0 minor: 0 level: 0 mag_min: -2000 mag_range: 12800 mag_steps: 256; stars: 5013
ZoneArray::create(/usr/share/stellarium/stars/default/stars_1_0v0_0.cat): type: 0 major: 0 minor: 0 level: 1 mag_min: 6000 mag_range: 12800 mag_steps: 256; stars: 21999
ZoneArray::create(/usr/share/stellarium/stars/default/stars_2_0v0_0.cat): type: 0 major: 0 minor: 0 level: 2 mag_min: 7500 mag_range: 12800 mag_steps: 256; stars: 151516
ZoneArray::create(/usr/share/stellarium/stars/default/stars_3_0v0_0.cat): type: 1 major: 0 minor: 0 level: 3 mag_min: 9000 mag_range: 1500 mag_steps: 30; stars: 434064
finished, max_geodesic_level: 3
Loading location: "Paris", on EarthLoading NGC data... (13226 items loaded [3175 dropped])
Loading NGC name data...
...no position data for Barnard's galaxy
...no position data for Papillon
...no position data for &#947; Cas nebula( 226 names loaded)
Loading Nebula Textures for set default...(109 textures loaded)
Loading Constellation boundary data from /usr/share/stellarium/data/constellations_boundaries.dat ...
(782 segments loaded)
Load star names from /usr/share/stellarium/skycultures/western/star_names.fab
Load sci names from /usr/share/stellarium/stars/default/name.fab
Loading Cities data for planet Earth...(2069 cities loaded)
Localizing TUI for locale: en_PH.
Script completed.
Segmentation fault (core dumped)

Should I reinstall?

---

### Post by jespdj on 2007-11-27
It works on my desktop and laptop without problems, both running Ubuntu 7.10 and both having nVidia video cards.

What graphics card does your computer contain? Are 3D graphics supported? Which graphics driver are you using? Do Compiz Fusion desktop effects work?

Alternatively you could try Google Earth, which also has a planetarium built-in. You can get Google Earth for Ubuntu from [Medibuntu]("http://www.medibuntu.org/").

---

### Post by kstella on 2007-11-27
My graphics card is some generic card that was came with the computer package, but as far as I can tell, it can support 3D graphics; when I was running windows, I could play The Sims 2. :p

---

### Post by staticvoid on 2007-11-27
make sure compiz or beryl is not running. work for me with metacity.

sv

---

### Post by kstella on 2007-11-27
> **staticvoid said:**
> make sure compiz or beryl is not running. work for me with metacity.

sv

It's not. :(

---

### Post by jespdj on 2007-11-27
> **kstella said:**
> My graphics card is some generic card that was came with the computer package, but as far as I can tell, it can support 3D graphics; when I was running windows, I could play The Sims 2. :p
You need to find out what brand it is and what video driver you are using. Do the Compiz desktop effects settings work at all on your computer or not? If not, then there's a good chance that (1) you don't have good graphics drivers or (2) the video card is not powerful enough.

Try the command "lspci" to get a list of PCI devices in your computer. Your video card should appear in that list. Have a look and tell us exactly what video card is in your computer.

You don't need to switch off Compiz to get Stellarium to work. I have Compiz desktop effects on both my computers and Stellarium works without fiddling with Compiz.

You can also try to get support on [http://stellarium.org/](http://stellarium.org/)

---

### Post by kstella on 2007-11-27
That's Preferences > Appearance > Visual Effects, right?

They could not be enabled. Aww... :(

---

### Post by kstella on 2007-11-27
This is it:

*01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]*

---

### Post by daveoftheworld on 2008-01-20
i had a similar problem an i opened a terminal and typed:gksudo stellarium   then i pressed enter. then i typed my password and then it ran fine. otherwise if i started it from applications:education:stellarium, it would only pop up a small termial type of window for about 1 second and if i looked with system monitor there was no instance of stellarium running. hope this helps.

---

