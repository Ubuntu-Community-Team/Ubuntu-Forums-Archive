---
title: "How can I set a gif as my Desktop backround?"
date: 2014-12-20
forum: General Help
---

### Post by josh109 on 2014-12-20
I know that there are other posts, but nothing seems to work. I have a gif that I want to set as my desktop backround, does anyone know how to do this?
Thanks in advance!
](*,)

---

### Post by yay101 on 2014-12-21
I used to use xwinwrap for this, i used to have mplayer play a random video from my server without sound. People thought it was incredible.

---

### Post by HereInOz on 2014-12-21
You can set any image or group of images as a desktop background using Shotwell.  Select the picture or pictures in Shotwell, click on File and Set as desktop background or slideshow.

---

### Post by josh109 on 2014-12-21
> I used to use xwinwrap for this, i used to have mplayer play a random  video from my server without sound. People thought it was incredible.
I couldn't get xwinwrap to work.

---

### Post by josh109 on 2014-12-21
> **HereInOz said:**
> You can set any image or group of images as a desktop background using Shotwell.  Select the picture or pictures in Shotwell, click on File and Set as desktop background or slideshow.
Shotwell does not allow me to set a .gif file as my desktop backround.

---

### Post by Bashing-om on 2014-12-21
josh109; Hello;

Nope, no can do with a .gif image:
> 
Create or resize any image to to the appropriate size.
GRUB 2 currently supports PNG, TGA, and 8-bit JPG/JPEG images.


Convert the gif image to one that is supported.
See:
[https://help.ubuntu.com/community/Grub2/Displays#Configuration_settings_.28splash_image_present.29](https://help.ubuntu.com/community/Grub2/Displays#Configuration_settings_.28splash_image_present.29)
for full details and howto.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by josh109 on 2014-12-22
> **Bashing-om said:**
> josh109; Hello;

Nope, no can do with a .gif image:


Convert the gif image to one that is supported.
See:
[https://help.ubuntu.com/community/Grub2/Displays#Configuration_settings_.28splash_image_present.29](https://help.ubuntu.com/community/Grub2/Displays#Configuration_settings_.28splash_image_present.29)
for full details and howto.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]

I'm sure there's a way to set a *moving image* as the desktop, I've seen it before. I just can't figure out how...

---

### Post by bfmetcalf on 2014-12-22
You can try [http://www.lcdf.org/gifsicle/](http://www.lcdf.org/gifsicle/) and use ```
gifview --animate --new-window root  animated.gif
``` and see if it works

---

