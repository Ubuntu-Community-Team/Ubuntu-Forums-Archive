---
title: "Resolution woes"
date: 2013-06-05
forum: General Help
---

### Post by MarcusA on 2013-06-05
After a short pause from using Ubuntu, I've come back and now have Ubuntu 13.04 installed. But I'm having a problem setting the correct screen resolution. It should be set at 1280x768, but for the life of me I cant find how to do it. Currently I have it set at 1024x768, but that streches it out a bit and all it does is give me a headache. The other available resolutions cut off parts of the screen. Please help.

xrandr -q:

```
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 700mm x 390mm
   1280x720       60.0 +   75.0     59.9     50.0  
   1920x1080      59.9     50.0     30.0     30.0     25.0  
   1280x1024      75.0     60.0  
   1024x768       75.0     70.1     60.0* 
   1024x576       75.0     60.0  
   848x477        75.0     60.0  
   800x600        75.0     72.2     60.3     56.2  
   800x500       120.0  
   720x576        50.0  
   720x480        59.9  
   640x480        75.0     72.8     59.9     59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)


```

---

### Post by MarcusA on 2013-06-05
Also when I do 

cvt 1280 768:

```
1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```

Is what I get, so then I did:

```
 xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```

and:

```
xrandr --addmode HDMI-0 1280x768_60.00
```

But it tells me this:

```
Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40
```

---

### Post by MarcusA on 2013-06-05
Anyone?

---

### Post by QIII on 2013-06-05
Hello, MarcusA!

Please remember that the Forum is populated by people all around the globe.  The person with the best answer may live in Taipei, Cape Town or Des Moines.  They have lives and are not always here.  Everyone here is a volunteer and is here as they have time.

Please wait 24 hours before bumping a thread.    I'm sure you are going to get an answer well before that, however.

Thanks!

---

### Post by MarcusA on 2013-06-06
^
It was just a little "before-going-to-bed-bump"
> **QIII said:**
> They have lives and are not always here.

How selfish of them! [-(

---

### Post by MarcusA on 2013-06-07
3 cookies for a solution

---

### Post by MarcusA on 2013-06-09
Surely someone must have an answer?

---

### Post by MarcusA on 2013-06-10
[IMG]http://linkplein.net/viewImage.php?id=143[/IMG]

---

### Post by MarcusA on 2013-06-11
bumps

---

### Post by TNFrank on 2013-06-11
Just a shot in the dark here but I noticed in Jupiter there's some resoultions settings.  I downloaded it for the power management but you can also see your CPU temp and like I said, adjust screen resoultion from it. Might give it a try, may work may not. I'm still a noob my self and still trying to figure this stuff out.

---

### Post by MarcusA on 2013-06-11
^ 
Tried it, but no luck :(

---

### Post by MarcusA on 2013-06-12
Badumpabump

---

### Post by Iowan on 2013-06-12
I presume you've seen [this]("https://wiki.ubuntu.com/X/Config/Resolution") wiki page...

---

### Post by carboi82 on 2013-06-12
2 quick quesions... You say the res should be 1280x768... I assume from that youve had the same hw setup running without issue at that before? Also, are you using the included video drivers, or third-party ones (fglrx)?

---

### Post by MarcusA on 2013-06-12
> **Iowan said:**
> I presume you've seen [this]("https://wiki.ubuntu.com/X/Config/Resolution") wiki page...

Yes, it results in that error which I have posted in my second post.  I very well may be doing it completly wrong.. (most likely :D)

> **carboi82 said:**
> 2 quick quesions... You say the res should be 1280x768... I assume from that youve had the same hw setup running without issue at that before? Also, are you using the included video drivers, or third-party ones (fglrx)?

Yes, about a year ago I could use it, I had a different computer back then though and used VGA instead of HDMI. It does work on windows 7. I am using the nvidia-313 drivers.

---

### Post by HiImTye on 2013-06-12
1280×768 is a 15:9 resolution, which won't scale properly on most (if not all) monitors. are you sure you don't mean one of:
4:3
```
1024×768, 1280x1024
```
16:9
```
1024x576, 1280x720, 1920x1080
```16:10
```
1280×800
```[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by MarcusA on 2013-06-13
^
Yeah, I'm sure. I am now using 1024x768 since at least everything is vissible on my screen, but everything is streched out.

---

### Post by MarcusA on 2013-06-14
bumps

---

### Post by cwsnyder on 2013-06-15
You may have to wait for an update to the nVidia driver for Linux.  From the error message on xrandr, nVidia seems to indicate that the requested resolution is not supported.  Or you could always use an older driver and see if that supports your display better.

---

