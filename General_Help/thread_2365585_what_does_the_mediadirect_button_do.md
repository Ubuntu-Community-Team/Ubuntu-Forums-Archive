---
title: "what does the mediadirect button do?"
date: 2017-07-08
forum: General Help
---

### Post by ardouronerous on 2017-07-08
I installed Lubuntu 16.04 on my dad's old Dell Inspiron E1505 laptop, and there's a button labeled MediaDirect.

[IMG]http://philipyip.files.wordpress.com/2014/03/media-direct.jpg[/IMG]

---

### Post by wildmanne39 on 2017-07-08
This is what it does:
> If you computers off it will launch a special mini OS just for pictures, music and the like. If its on it will load a media program that does much the same call Dell Media Direct.
it only works with windows and you have to have specific programs installed.

---

### Post by ardouronerous on 2017-07-08
okay, thanks for that info, what happens if this button is pressed on Lubuntu?
is there anyway to remap this button to be useful on Lubuntu?

---

### Post by vasa1 on 2017-07-08
> **ardouronerous said:**
> okay, thanks for that info, what happens if this button is pressed on Lubuntu?
is there anyway to remap this button to be useful on Lubuntu?
[center]*****
Warning! There are links indicating that this button could be dangerous on Linux systems! Search for "dell mediadirect key linux"
*****[/center]

Possibly!

You'll first need to find out how the system "sees" that key. Open *lxterminal* and paste in the following code:```
xev | grep -m 1 -A 2 "KeyPress event" | sed -n '3p' | awk -F'[,() ]+' '{ print $4 " " $5 "; " $6 " " $7 "; "$8 }'
```and press *enter*. You'll see a small white window appear. Now, without doing anything else, press the key of interest. The window will close and you'll get some output in the terminal.

Paste that here.

---

### Post by johndough2 on 2017-07-08
Hi

I don't know.

But when I bought a dell laptop it was to play media direct, ie: a dvd from the player without booting the full OS.

There was a small separate software area to just play dvd's.

[http://www.dell.com/support/home/uk/en/ukbsdt1/Drivers/DriversDetails?driverid=R107182](http://www.dell.com/support/home/uk/en/ukbsdt1/Drivers/DriversDetails?driverid=R107182)

It's a Windows thing, but whether the button is still valid with Lubuntu installed I don't know.
###########
If you hold the media control play button for longer than two seconds while you are logged in, Dell MediaDirect launches Microsoft Windows Media Center Edition or Dell Media Experience, ***_depending on your system setup. _***If both applications are present, Windows Media Center Edition will launch.

When your computer is open, you can press the media control play button to start the computer from any state and automatically launch the media application.
##############

---

