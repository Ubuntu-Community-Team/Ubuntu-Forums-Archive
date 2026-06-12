---
title: "Resolution help!"
date: 2007-08-28
forum: General Help
---

### Post by Depressed Man on 2007-08-28
Well I went from a 17 inch to a 19 inch widescreen. When I switched monitors (After inputting a command that I now forgot) it correctly detected my new monitor and the resolution for it (the highest is 1400 x 900 which is what I use).

Ok, so I shutdown Ubuntu, boot into XP for a while to play some Guild Wars. I go back to Ubuntu and for some reason the resolution is now stuck at 1280x1024 or something like that. And for the life of me I cannot get it back to the 1400x900. Looking at the xorg.conf it says 1400x1400 then 1280x1024, then so on. 

I even tried virtual 1400 900 but that just buggered GDM so I had to use the command line (god how useful this is) to remove it. 

Any help? Please?

---

### Post by nitro_n2o on 2007-08-28
did you try 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wolfger on 2007-08-28
> **Depressed Man said:**
> And for the life of me I cannot get it back to the 1400x900. Looking at the xorg.conf it says 1400x1400 then 1280x1024, then so on. 

I assume you meant that xorg.conf says 1400x900, not 1400x1400?
If not, try correcting it to 1400x900.

Also, I don't know about you, but my conf has multiple color depths, and a resolution line for each. Make sure the line corresponding to your DefaultDepth has the resolution you want. Example:
```
Section "Screen"
  Identifier  "Default Screen"
  Device    "S3 Inc. ProSavage KN133 [Twister K]"
  Monitor   "Generic Monitor"
  DefaultDepth  24
  # Skipping some text to improve readability
  SubSection "Display"
    Depth   24
    Modes   "1400x900"
  EndSubSection
EndSection
```

---

### Post by Depressed Man on 2007-08-28
> **nitro_n2o said:**
> did you try 
```
sudo dpkg-reconfigure xserver-xorg
```

I'll try that again. 

It was 1400x1400 but I tried adding 1400x900 behind it (before the 1280x1024 entry). But I added it in all the depths.

---

### Post by wolfger on 2007-08-28
> **Depressed Man said:**
> It was 1400x1400 but I tried adding 1400x900 behind it (before the 1280x1024 entry). But I added it in all the depths.
Also you might try reducing the default depth. I don't recall the specifics, but I remember that I had some issues once with trying to set my depth too high, and I couldn't get the resolution I wanted. Reducing the depth allowed me to get my resolution.

---

### Post by nitro_n2o on 2007-08-28
a 19" wide screen should handle depth up to 24 this should not be a problem.. problems occur with refresh rates you need to have them correct... and if you still have troubles what is your graphics card?

---

### Post by Depressed Man on 2007-08-28
Well I accidently messed up my system (well not really I just have to find a way to get into a terminal). But I deleted all other modes and just left in the one I wanted "1400x900" (though I later realized I wanted 1440x900). And now when Ubuntu loads up the monitor says frequency out of range (though I can use safe mode to get back in right?)

Anyway I'm using an ATI x800 Saphiere Radeon. Using the open source drivers I believe (restricted isn't used).

---

### Post by Depressed Man on 2007-08-29
Ok I got it up and running again. Though I have a question. Each time I turn my monitor off (say when I leave the computer) and turn it back long it has to autoreconfigure. But it doesn't do this in Windows.

---

