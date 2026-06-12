---
title: "Incorrect detection of screen size?"
date: 2021-07-11
forum: General Help
---

### Post by linuux on 2021-07-11
Sorry, I don't know what to input in the (Advanced) Search field for this.   I tried booting up 21.04 iso of Ubuntu and Kubuntu.

In System Settings - display settings - Ubuntu detects my 4k tv as 36"

Kubuntu displays the brand and model name '50' is in the model name so I initially thought, 'hey, Kubuntu is displaying the correct info, Ubuntu isn't'

But, I think this was not accurate, ultimately.

I ran the xrandr and hwinfo commands.

In one of the lines was '800mm x 450mm' - does that mean it detected it as a 32" screen?  I am confused.  I couldn't find any good programs/commands that output more detailed info of the TV display hardware.  Yes, the resolution and refresh rates were output so plenty of info on that.  But, I was looking for an output that displayed the dimensions of the TV.   The TV brand and model was displayed but I wanted output of the screen size - e.g. '50"' or even 49.x would be acceptable.  

I think the measurements in mm was the detection/display of the screen dimensions?   But, they are incorrect/inaccurate.

Is that something to be concerned with when I install?   Or is the programs just not detecting it correctly?   Am I missing something?   This is with live media - but, I don't expect it to be a different result with an actual install written to disk.   Why would there be?

Any ideas?  When I researched this, I mostly found people asking why 'the resolution' was detected, inaccurately/incorrectly.   That's not my problem or issue.  Maybe it's inconsequential?

My hardware:   TCL 50" 4K TV, Dell Optiplex 3020 sff, using Intel igpu HD 4600... xrandr and hwinfo provided info on the TV brand/model, intel igpu info and the rest of the hardware.   Just no mention of the screen size unless that number above '800mm vs 450mm' is what it detected?  I couldn't find any other measurements after entering those CLI commands.

---

### Post by CatKiller on 2021-07-11
The computer only knows what the display tells it; your computer doesn't get out a tape measure. The mechanism for displays to advertise their capabilities is called EDID. Your display is lying in its EDID. Either because they've refused the EDID from a different model, or they're trying to fudge automatic DPI calculations, or something of that nature.

---

### Post by linuux on 2021-07-11
> **CatKiller said:**
> The computer only knows what the display tells it; your computer doesn't get out a tape measure. The mechanism for displays to advertise their capabilities is called EDID. Your display is lying in its EDID. Either because they've refused the EDID from a different model, or they're trying to fudge automatic DPI calculations, or something of that nature.Yes, I'm aware of that - that the programs are just 'fetching' what the tv programming 'provides them.'   I thought it might be something like that.   Just wanted to confirm. 

I did read about the EDID program but I didn't think the output was any better than hdinfo.  Perhaps, I am incorrect about that then.

Anyway, I guess it is of little consequence but does this mean that all/most TV manufacturers are 'lying' or providing inaccurate EDID info?  I don't see what reason the manufacturer would provide incorrect screen size.

---

### Post by TheFu on 2021-07-11
The TV sends whatever it wants to the GPU.  If it lies, then you'll see those lies.  This only works for digital connections as far as I know - so dvi-i or hdmi.  I don't have DP, so don't KNOW what that does, but I'd expect DP would show the same as HDMI shows. VGA communicates only enough to prevent the GPU from over-driving the monitor and killing it.  That was a concern in the early 1990s.

```
sudo get-edid | parse-edid
```
Shows what the GPU is told.  If there are any converters or KVMs between the GPU and the monitor, expect those to be shown. Si?
For example, 
```
Section "Monitor"
        Identifier "DELL U2412M"
        ModelName "DELL U2412M"
        VendorName "DEL"
        # Monitor Manufactured week 10 of 2013
        # EDID version 1.3
        # Analog Display
        Option "SyncOnGreen" "true"
        DisplaySize 520 320
        Gamma 2.20
        Option "DPMS" "true"
        Horizsync 30-83
        VertRefresh 50-61
```
but going through a powered DVI-I -to- VGA converter to the same monitor (KVM switch), I see:
```
Section "Monitor"
        Identifier "\&#65533;"
        ModelName "\&#65533;"
        VendorName "AGO"
        # Monitor Manufactured week 45 of 2013
        # EDID version 1.3
        # Digital Display
        DisplaySize 300 230
        Gamma 1.97
        Option "DPMS" "true"
```
The 2nd answer is about the converter device, not the actual monitor.
The monitor does say "Dell" on the front and I think it is a 24 inch 1920x1200p @ 60hz model. [https://www.dell.com/is/business/p/dell-u2412m/pd](https://www.dell.com/is/business/p/dell-u2412m/pd)  It has been a good monitor. Replaced a Gateway 24inch that died 1 day.  I've been looking at 4K options the last few months, but decided to wait for better quality to get cheaper based on some feedback from about 15 friends.

---

### Post by ianwhite7 on 2021-08-12
Only way for computer to calculate it's display size is if it knew it's pixel density measurement called [ppi]("https://screenresolutiontest.com/")(pixel per inch).
It could then divide its horizontal and vertical resolution in physical pixels with ppi to get its size in inches.

---

