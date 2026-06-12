---
title: "Colour calibration"
date: 2016-01-21
forum: General Help
---

### Post by NaneK on 2016-01-21
Hi everybody,

I noticed that colours on Ubuntu look different than on Windows, on  the same laptop. The problem is that when I use Photoshop in Virtualbox  and I make a solid colour image in one colour, and when I view it on a  host OS (Ubuntu), the colour looks different. I work as a web designer,  and this bugs me, because stuff doesn't look the same.


  Let me show it to you.
  [[IMG]http://i.stack.imgur.com/uUfIT.png[/IMG]]("http://i.stack.imgur.com/uUfIT.png")

  This is part of my website as viewed in Virtualbox Windows. You can  notice that all of the green lines look the same. Top line is defined in  CSS, and the shape below it is a PNG image. Colours are the same.


  Now, lets see how that looks in Ubuntu.
  [[IMG]http://i.stack.imgur.com/L7gm0.png[/IMG]]("http://i.stack.imgur.com/L7gm0.png")
  The top line (CSS defined) is the same, but the image below changes its colour to a more vivid tone. 


  The screen is not the problem since this doesn't happen in Virtualbox on Windows, only on Ubuntu (host OS).
  Is there any way to calibrate colours on Ubuntu, like it's possible on Windows?


  I tried the Colours app in System settings, but the Calibrate button  is greyed out, I can't click on it, and other options do not provide any  calibration.
  Since it's a laptop I can't do it manually, so it has to be done via software. I am using Ubuntu 14.04 LTS.

---

### Post by mcduck on 2016-01-21
I assume the image in question is a PNG file? PNG's cans tore olor profile information, in which case they might look wrong on non-calibrated displays.

What comes to color calibration on Ubuntu, you need to use a calibrator. There's no way to do it by eye. However if you have .icc file (either from your Windows side, or a factory default one from the manufacturer), you can just copy that over to Ubuntu and use it.

(however since most people don't have color-calibrated displays anyway, or might be using wrong calibration, I'd usually just recommend stripping the color profile information from any PNG files you want to use on web pages).

---

### Post by NaneK on 2016-01-22
Thanks man, that solved the problem.
I replaced my PNG images with new ones, without color profile, and it's great now.

Since I was using Photoshop (in Virtualbox) for that, here's the way I have done that (in case someone search for something like this):

Answer is to open (in Photoshop) every PNG  image (that causes problems) and then copy it (CTRL+A -> CTRL+C).  Then create new image in Photoshop (CTRL+N), and in settings of new  image under Advance tab change Color profile from "sRGB ..." to "dont  color manage this document".  Now my PNG images look the same on Ubuntu  and Windows.

---

