---
title: "Edgy reverts refresh rate"
date: 2006-10-27
forum: General Help
---

### Post by Spif on 2006-10-27
Every time I restart the X server, Edgy reverst my refresh rate from 60 to 75 Hz. This is a bit annoying, as I have to manually set it to 60 Hz everytime I log on.

I'm using the "nv" driver, as the "nvidia" doesn't allow me to set the frequency at all. Can anyone help me fix this?

---

### Post by reclusivemonkey on 2006-10-27
> **Spif said:**
> Every time I restart the X server, Edgy reverst my refresh rate from 60 to 75 Hz. This is a bit annoying, as I have to manually set it to 60 Hz everytime I log on.

I'm using the "nv" driver, as the "nvidia" doesn't allow me to set the frequency at all. Can anyone help me fix this?

What is your monitor's refresh rate, and what do you have in your xorg.conf's  
Section "Monitor"?

---

### Post by GortBlimey on 2006-10-27
I had a similar problem when using the Nvidia module in Dapper. I fixed it by passing "sudo nvidia-xconfig --mode 1280x1024_60" (no quotes)into a console/xterm (change the amounts for your particular monitor). Do backup your xorg.conf file first, though.

---

### Post by Spif on 2006-10-28
> **GortBlimey said:**
> I had a similar problem when using the Nvidia module in Dapper. I fixed it by passing "sudo nvidia-xconfig --mode 1280x1024_60" (no quotes)into a console/xterm (change the amounts for your particular monitor). Do backup your xorg.conf file first, though.

Unfortunately, this didn't work :(

> **reclusivemonkey said:**
> What is your monitor's refresh rate, and what do you have in your xorg.conf's  
Section "Monitor"?

Refresh should be 60 Hz, but every time I restart X, it gets reset to 75. This is using the "nv" driver. With the "nvidia", I can't change refresh rate at all.

```
Section "Monitor"
    Identifier     "170EI-A01-V5"
    Option         "DPMS"
EndSection
```

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "170EI-A01-V5"
Option "AddARGBGLXVisuals" "True"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

### Post by reclusivemonkey on 2006-10-28
> **Spif said:**
> 
Refresh should be 60 Hz, but every time I restart X, it gets reset to 75. This is using the "nv" driver. With the "nvidia", I can't change refresh rate at all.

```
Section "Monitor"
    Identifier     "170EI-A01-V5"
    Option         "DPMS"
EndSection
```


Try adding your refresh rates to this section. You should be able to find these in your monitor manual, or on the manufacturers website. For my CRT monitor I have;

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       50.0 - 160.0
    VertRefresh     30.0 - 80.0
    Option         "DPMS"
EndSection

```

---

### Post by Spif on 2006-10-30
Can't find any information about what values I should write in my xorg.conf. The screen manufacturer Orion doesn't exist anymore and it is quite some time ago that I threw away the manual. 

Anyone know what the correct values could be?

---

### Post by puggers on 2006-11-22
I have both the same graphics card and the same monitor as you (well the and the same Identifier number anyway, so i guess its the same). 
I also had the same troubles with there not being an option to change the refresh rate using the nvidia driver, but the "sudo nvidia-xconfig --mode 1280x1024_60" command fixed it. So i assume if you switch back to using the nvidia driver instead of the nv one, and then use the command, it will work for you also. 

I'm aware you are probably long gone now, but i thought i should say it anyway! thanks GortBlimey for the solution!

---

