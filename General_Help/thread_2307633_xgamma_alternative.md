---
title: "xgamma alternative?"
date: 2015-12-26
forum: General Help
---

### Post by ultragamer2 on 2015-12-26
I have a mini arm computer but due to it's simple graphics chip commands using xgamma (eg. xgamma -bgamma 1.5) don't work.

Is there any other way to apply gamma changes with hardware accelerated video? (probably not I guess)

---

### Post by PhilGil on 2015-12-26
Not sure if this will work successfully on an ARM processor, but you can also set gamma using xrandr, i.e.
```
xrandr --output *output-name* --gamma 1.0:1.0:1.0
```

Find your output name with this command:
```
xrandr --verbose
```
For example, on my PC the output name is HDMI1 from this line:
"HDMI1 connected primary 1920x1080+0+0 (0x45) normal (normal left inverted right x axis y axis) 510mm x 287mm"

Gama setting is in r:g:b order. Decrease values (in steps of 0.1) to increase contrast, Increase values (in steps of 0.1) to decrease contrast.

---

### Post by ultragamer2 on 2015-12-27
Thanks here is the output, what should I type exactly?

```
odroid@odroid:~$  xrandr --verbose
Screen 0: minimum 640 x 480, current 1920 x 1080, maximum 2048 x 2048
LCD connected primary 1920x1080+0+0 (0x40) normal (normal) 0mm x 0mm
    Identifier: 0x3f
    Timestamp:  185342
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1920x1080 (0x40)  139.2MHz *current
        h: width  1920 start 1940 end 1960 total 2000 skew    0 clock   69.6KHz
        v: height 1080 start 1100 end 1120 total 1160           clock   60.0Hz
```

---

### Post by PhilGil on 2015-12-27
Your output name is "LCD", so you'll want to type this
```
xrandr --output LCD --gamma 0.9:0.9:0.9
```
That should make your screen appear more contrasty. You can play around with the numbers to get the best results. The changes aren't permanent (they will only last for the current session) so you can't mess anything up that a reboot won't fix.

---

### Post by ultragamer2 on 2015-12-27
Thanks, unfortunately it doesn't seem to recognise Screen 0

```
xrandr --Screen 0 --gamma 0.9:0.9:0.9
```

I also tried

```
xrandr --output Screen 0 --gamma 0.9:0.9:0.9
```

Am I phrasing the syntax wrong?

---

### Post by PhilGil on 2015-12-27
> **ultragamer2 said:**
> Thanks, unfortunately it doesn't seem to recognise Screen 0

xrandr --Screen 0 --gamma 0.9:0.9:0.9

I also tried

xrandr --output Screen 0 --gamma 0.9:0.9:0.9

Am I phrasing the syntax wrong?

So you're saying that typing exactly what I posted previously ("xrandr --output LCD --gamma 0.9:0.9:0.9") didn't work?

---

### Post by ultragamer2 on 2015-12-27
Oh yeah I tried that too. It didn't give any error but nothing changed on the screen.
So I tried changing the values to 2.0:0.1:0.1 but there was still no change. It must be incompatible with the Mali graphics chip.

---

### Post by PhilGil on 2015-12-27
> **ultragamer2 said:**
> Oh yeah I tried that too. It didn't give any error but nothing changed on the screen.
So I tried changing the values to 2.0:0.1:0.1 but there was still no change. It must be incompatible with the Mali graphics chip.
Sorry to hear that didn't work. I'm out of ideas. Unless someone else on the forum can help you're probably right about your graphics being incompatible.

---

### Post by ultragamer2 on 2015-12-28
Thanks for your help, at least I know what to type if I get another mini computer that is compatible.

Does anyone know what is the cheapest / lowest power using mini computer I can buy that definitely would be compatible with this command or "xgamma - rgamma 0.5" etc. and that can play videos up to 1080p from a usb stick?
Or if not a specific computer model, what should I look for in a graphics chip so I don't make the same mistake of buying another one that is not compatible with gamma commands.

---

