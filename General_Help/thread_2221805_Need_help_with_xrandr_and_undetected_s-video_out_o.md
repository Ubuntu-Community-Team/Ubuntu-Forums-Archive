---
title: "Need help with xrandr and undetected s-video out on Lubuntu 14.04"
date: 2014-05-03
forum: General Help
---

### Post by Tony_Lillie on 2014-05-03
As usual I'm posting after spending at least 2 hours researching and trying to find the answer on my own. Apparently each situation with display configurations, X, xrandr and the like is unique and therefore finding answers is very difficult without some assistance from experienced users.

I have a 10 year old HP zv6000 laptop running Lubuntu 14.04 and the s-video is detected, but it reports being disconnected even when I have my TV connected to it. When I run ```
xrandr
``` I get the following output ```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 330mm x 210mm
   1280x800       60.1*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
**S-video disconnected** (normal left inverted right x axis y axis)

```
I also tried ```
[COLOR=#333333]xrandr --output S-video --set load_detection 1[/COLOR]
``` but got the following error ```
X Error of failed request:  BadName (named color or font does not exist)  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  29
  Current serial number in output stream:  29
```
Though I am not a beginner to Linux, I am a beginner to dealing with X and xrandr. I've been fortunate that all of my various Linux installations have never had a single display issue. 

I would greatly appreciate some experienced help. I need to get this s-video output working, even if it merely clones the primary laptop display, but I really don't know where to start.

---

### Post by sudodus on 2014-05-04
I hope someone can help you get it working in Lubuntu 14.04 LTS.

Otherwise there are workarounds: You can install a light-weight re-spin or distro based on Ubuntu 12.04 LTS, which has several years to end of life: ***Bento, Bodhi*** or ***LXLE***. (Standard Lubuntu 12.04 has passed end of life).

See also this link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by Tony_Lillie on 2014-05-04
I'm cool with an earlier distro, as long as it really is a path to success. The end (a working s-video to TV) will justify any means at this point. Reading your link now...

---

### Post by sudodus on 2014-05-04
The first post of that link, [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640"), is the most important one, but I suggest that you read several other posts, for example post #40

[http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552](http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12918552#post12918552)

and the posts around it.

---

### Post by Tony_Lillie on 2014-05-08
Still no joy after reading everything I can find and trying a variety of things. Could really use some additional help here. Is it really that difficult to configure an S-video out port. I really hate to do it, but if I install XP I know it will "just work". Is that my only option??

---

### Post by sudodus on 2014-05-08
Did you try a flavour or re-spin based on Ubuntu 12.04 LTS?

- Xubuntu 12.04 LTS
- Bento, Bodhi or LXLE

I remember that it worked with Ubuntu 10.04 LTS in my old IBM Thinkpad T41, and I have not tried it in 12.04 LTS. I gave the T41 to a friend, but have a T42 now. Maybe I can find hardware to test it ...

Running Lubuntu 14.04 LTS:

S-video 'works out of the box' from my IBM Thinkpad T42 to a video projector, that can use it via an S-video to composite video (yellow RCA) adapter. The system reset the resolution to the built-in screen from the default 1024x768 to 800x600 (which is the resolution of the projector). 

I don't know why it works for me but does not work for you. Let us hope someone who knows more about S-video will chip in and help you.

---

