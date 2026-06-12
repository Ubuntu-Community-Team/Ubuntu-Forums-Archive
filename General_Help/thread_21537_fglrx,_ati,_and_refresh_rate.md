---
title: "fglrx, ati, and refresh rate"
date: 2005-03-22
forum: General Help
---

### Post by kb00heda on 2005-03-22
I recently installed the fglrx drivers, and they seem to work fine. 

First I was wondering about the old ati drivers: If I wanted to revert back, would it be as simple as to use the old /etc/X11/xorg.conf file again? It seems so. No need to unistall "fglrx"?  The two drivers may co-exist?

Second, if I wanted to configure the /etc/X11/xorg.conf file, in order to manually change the refresh rate on my screen, can I look in /var/log/Xorg.0.log file, and take a given modeline to add in xorg.conf's Monitor section? I had, e.g., this modeline

```
(**) fglrx(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
```

which would give me 1280x1024@85Hz if I added it?

Third, is it necessary to add in the Device section the option 

"UseInternalAGPGART" "no"

and if so why?

Regards,
David

---

### Post by alastair on 2005-03-22
You can safely use the old xorg.conf fille (ati) - no need to uninstall anything. It will just use the opensource drivers. Switch between them (via the files) safely.

Modelines and refresh frequencies are slightly more complex probably. I used a program called "gtf" in the past, to calculate a modeline for inclusion to the config file :

[http://gtf.sourceforge.net/](http://gtf.sourceforge.net/)

Simple to compile and run - producing a "modeline" to add to the config file. Be careful though.

As for AGP - I wouldn't worry about it. The ATI firegl's can use internal or external - but with the same effect (hopefully). If things are working, leave them be.

---

### Post by kb00heda on 2005-03-23
Thanks for your reply! 

Good to know that both drivers can be used. The gtf program sounds like interesting. I had 1280x1024@100Hz when I used Windows, but, under Linux (so far SuSE and Ubuntu), I have yet to reach the same refresh rates; them ranging from 65-85 Hz seems to be the only -- at least by default -- choiche.

After checking my monitor specifications, just to make sure, I think I will give it a go; run gtf and try to adjust my settings to 1280x1024@100Hz. I will keep a copy (good habit before changing any configuration files) of /etc/X11/xorg.conf though, in case anything ... well ... backfires!  :smile:

/David


EDIT 1.

I just downloaded gtf and compiled it as it is says on the homepage. Then I ran

/.gtf 1280 1024 100

and got my modeline printed in the terminal. Just added that line

```
Modeline "1280x1024_100.00"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
```
in /etc/X11/xorg.conf last in the "Monitor" section. Rebooted the system and came back without a scratch. So, probably it worked, making me a happy camper!   :-D

---

### Post by Reb on 2005-03-30
You _should_ already have gtf with an Ubuntu install. Also, you only need to do a <Control><Alt><Backspace> to reset X, a full system reboot is unnecessary.

---

### Post by Ren on 2005-03-30
Back on Windows, I used 1280x960 @ 72hz, I want to use this refresh rate on here, but I only get 60hz, were exactly do I put the Modeline, Ive included a cut of my xorg config, everytime I try I end up with a error screen

```

Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 420]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "IBM E74"
        Option          "DPMS"
        #Modeline "1280x960_72.00"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV17 [GeForce4 MX 420]"
        Monitor         "IBM E74"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

---

### Post by J. S. Jackson on 2005-03-31
[QUOTE=kb00heda]
Third, is it necessary to add in the Device section the option 

"UseInternalAGPGART" "no"

and if so why?
[/QUOTE]

As far as I know, this is only neccesary if you have an nForce2 chipset.

---

### Post by Cool_dude_Prav on 2005-04-16
[QUOTE=alastair]You can safely use the old xorg.conf fille (ati) - no need to uninstall anything. It will just use the opensource drivers. Switch between them (via the files) safely.

Modelines and refresh frequencies are slightly more complex probably. I used a program called "gtf" in the past, to calculate a modeline for inclusion to the config file :

[http://gtf.sourceforge.net/](http://gtf.sourceforge.net/)

Simple to compile and run - producing a "modeline" to add to the config file. Be careful though.

As for AGP - I wouldn't worry about it. The ATI firegl's can use internal or external - but with the same effect (hopefully). If things are working, leave them be.[/QUOTE]
 Hey u ppl there...

gtf is not working for me and I am still on the same old 60Hz(*ouch*) refresh rate... :(

Please reply...

---

