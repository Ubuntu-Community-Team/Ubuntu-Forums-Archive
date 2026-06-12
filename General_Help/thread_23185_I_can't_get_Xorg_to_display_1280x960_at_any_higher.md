---
title: "I can't get Xorg to display 1280x960 at any higher than 60hz"
date: 2005-03-31
forum: General Help
---

### Post by Gnobody on 2005-03-31
I can't get X.org to display 1280x960 at any higher than 60hz on a Samsung 955DF with the appropriate Hsync and Vsync lines of 30-85 and 50-160 respectively.  I have had this problem on many distros not just Ubuntu for a year or more...  I am using the latest NVidia (non-free) drivers.

---

### Post by jdodson on 2005-03-31
[QUOTE=Gnobody]I can't get X.org to display 1280x960 at any higher than 60hz on a Samsung 955DF with the appropriate Hsync and Vsync lines of 30-85 and 50-160 respectively.  I have had this problem on many distros not just Ubuntu for a year or more...  I am using the latest NVidia (non-free) drivers.[/QUOTE]

i had the same problem.  basically from what i understand xfree86 does not support those resolutions even with the binary driver.  i upgraded to hoary and even with the free open source driver i could get WAY higher resolutions, like 1800x? at 75hz that warty.  where as i could only get 75hz running at 1024x768 in warty with the binary driver.  i checked and xorg updated MANY free drivers to the latest versions and it really helped the resolution and refresh for my video card and monitor.  now the proprietary 3D driver does not afford me higher resolutions as the free one, it just allows me to run 3D video.

so basically i recommend upgrading to hoary.  that might help you out.

---

### Post by MaX on 2005-04-01
[QUOTE=Gnobody]I can't get X.org to display 1280x960 at any higher than 60hz on a Samsung 955DF with the appropriate Hsync and Vsync lines of 30-85 and 50-160 respectively.  I have had this problem on many distros not just Ubuntu for a year or more...  I am using the latest NVidia (non-free) drivers.[/QUOTE]
 I had this problem once, I just commented out the Hsync Vsync lines and it autodetected the correct values (guess xorg asked the monitor)

---

### Post by Gnobody on 2005-04-01
lol, I have never tried that!  I'll give it a try when I get home.

What does the DPMS option do?

---

### Post by HungSquirrel on 2005-04-01
[QUOTE=Gnobody]lol, I have never tried that!  I'll give it a try when I get home.

What does the DPMS option do?[/QUOTE]
 DPMS allows the computer to shut off the monitor when the computer isn't in use.  It's a good idea to leave it in your config and to set up xscreensaver to power off the monitor after a certain amount of time to both save power and avoid burn-in.

---

### Post by Gnobody on 2005-04-01
[QUOTE=HungSquirrel]DPMS allows the computer to shut off the monitor when the computer isn't in use.  It's a good idea to leave it in your config and to set up xscreensaver to power off the monitor after a certain amount of time to both save power and avoid burn-in.[/QUOTE]
 k, thank you I won't remove DPMS 

 Removing the HorizSync and VertRefresh lines didn't change anything when I restarted my Xserver. :(

---

### Post by Kev0r on 2005-04-02
Hi there this is the monitor section from my xorg.conf. The HorizSync and VertRefresh where found on google to match my monitor.
Hope it's any help to you..

```

Section "Monitor"
Identifier "Generic Monitor"
[B]HorizSync 30-96
VertRefresh 50-180
[/B]Option "DPMS"
EndSection
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV31 [GeForce FX 5600XT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection
```

---

### Post by Gnobody on 2005-04-02
[QUOTE=Kev0r]Hi there this is the monitor section from my xorg.conf. The HorizSync and VertRefresh where found on google to match my monitor.
Hope it's any help to you..

```

Section "Monitor"
Identifier "Generic Monitor"
[B]HorizSync 30-96
VertRefresh 50-180
[/B]Option "DPMS"
EndSection
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV31 [GeForce FX 5600XT]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection
```[/QUOTE]



OK, that works if I use the nv opensource driver but not if I use the nvidia driver.

---

### Post by Gnobody on 2005-04-03
Does anybody know how to get this to work with the NVidia binary driver?

---

### Post by fackamato on 2005-04-03
[QUOTE=Gnobody]Does anybody know how to get this to work with the NVidia binary driver?[/QUOTE]

Well, I have a Samsung Syncmaster 957P, currently at 1280x960@85hz, this is my xorg.conf:

```
Section "Monitor"
	Identifier  "Monitor0"
	HorizSync   30-96
	VertRefresh 60-120
	Option "DPMS"
	DisplaySize 338 254

#       DisplaySize     270     203     # 1024x768 96dpi
#       DisplaySize     338     254     # 1280x960 96dpi
#       DisplaySize     338     270     # 1280x1024 96dpi
#       DisplaySize     370     277     # 1400x1050 96dpi
#       DisplaySize     423     370     # 1600x1400 96dpi
Modeline "1280x960_85.00"  149.43  1280 1376 1512 1744  960 961 964 1008  -HSync +Vsync

EndSection

```

```
Section "Screen"
    Identifier  "Screen0"
    Device      "nVidia Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       8
        Modes       "1280x960" "1024x768" "800x600" "640x480" "512x384"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

    Subsection "Display"
        Depth       15
        Modes       "1280x960" "1024x768" "800x600" "640x480" "512x384"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

    Subsection "Display"
        Depth       16
        Modes       "1280x960" "1024x768" "800x600" "640x480" "512x384"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

    Subsection "Display"
        Depth       24
        Modes       "1280x960" "1024x768" "800x600" "640x480" "512x384"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

#    Subsection "Display"
#        Depth       32
#        Modes       "1280x960" "1024x768" "800x600" "640x480" "512x384"
#        ViewPort    0 0  # initial origin if mode is smaller than desktop
#    EndSubsection

EndSection
```

---

### Post by sapo on 2005-04-03
So.. i ve searched google and asked a lot of people about it and in my monitor manual it says:

1280x960@66hz

So windows was "overclocking" my monitor.. and there's no way i can make it work with Xorg without "overclocking" it.. cause xorg doesnt allow manual refresh rate configuration..

So i m using 1152x864@75hz :(

---

### Post by Christmas on 2006-09-05
Why don't you go for 1280x1024@75Hz? It works for me, and I can't make it work at 1280x960@75Hz too.

---

