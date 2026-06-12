---
title: "Wrong Login Screen Logo Displayed"
date: 2013-04-28
forum: General Help
---

### Post by Dennis N on 2013-04-28
(affects Lubuntu 13.04 only, not prior releases)

Anyone  using Lubuntu 13.04 getting this logo for the login screen? (see camera screenshot attached). I would expect it should be the Lubuntu logo here as in previous Lubuntu releases using lightdm greeter. Something is wrong.

Configuration file at:
**/etc/xdg/lubuntu/lightdm/lightdm-gtk-greeter.conf** 
seems to point to the correct icon (lubuntu logo), but apparently is not being followed. 

relevant line:
**logo=/usr/share/icons/lubuntu/places/64/start-here.svg**

lightdm-gtk-greeter.conf does work to change the login screen background, however, so it  is not being ignored for that. [*Correction: to be accurate, I didn't change the greeter background by editing this config file. That was done by changing the symbolic link (lubuntu-default-wallpaper.png) to point to my choice. That means the line here (background= ) could actually be ignored, if the greeter background is defined elsewhere in the same way.*]

Any suggestions on how change to the proper icon?

Thanks.

---

### Post by zero2xiii on 2013-04-28
Hay,

Have you tried changing the background by editing the file? This should give a quick answer whether or not the file is used.

I have had a similar issue on 12.10 lubuntu but simply changing it and back again worked. So I am not sure what caused it.

Cheers

---

### Post by Dennis N on 2013-04-28
> **zero2xiii said:**
> Hay,

Have you tried changing the background by editing the file? This should give a quick answer whether or not the file is used.

I have had a similar issue on 12.10 lubuntu but simply changing it and back again worked. So I am not sure what caused it.

Cheers

Good suggestion;

Edited **/etc/xdg/lubuntu/lightdm/lightdm-gtk-greeter.conf** directly to change background to a solid color (background="#333333") and that change worked. [*not really - see EDIT below!*] So the file is not ignored (at least that line!).

It seems something else is controlling the logo. As to the little humanoid icon in the screenshot, I have been looking for it on the system. No luck.



*EDIT: Changing the background= line to a solid color actually gives a black background. Color #333333 was close to black and I thought it worked - tested again with a blue-gray (#486488), rebooted and the background remained solid black. However, it's still true the file is not ignored, otherwise the wallpaper should stay up.* Which raises the question, How do you get a solid color?

Still looking for the fix.

---

### Post by Dennis N on 2013-04-29
**FYI Update to Post #3:**

Login Screen Background Color **can** be set to a solid color if desired. Edit the same file referred to in post 3, but instead of background="#333333" as tried there, I found you must omit the quotation marks. Correct syntax is **background=#333333** (where #333333 is simply the hex code for the color).

The original question on the seemingly incorrect logo and how to change it to the Lubuntu logo which previously has appeared there (or to something else perhaps) has not been solved.

---

### Post by zero2xiii on 2013-04-30
Hay,

So I am not using 13.04 atm, but rather 12.04 so there might be a huge difference?. But I am missing that line from my config file... I falled back to 12.04 because of having to many issues with 13.04 and 12.10.

However my USER logo is that "humanoid" logo. Try changing you username's logo and see if that changes the image?

Cheers

---

### Post by Dennis N on 2013-04-30
> **zero2xiii said:**
> Hay,

However my USER logo is that "humanoid" logo. Try changing you username's logo and see if that changes the image?

Cheers

Thanks for the reply. 

Where do I find, set or change the USER or username's logo? I didn't know that there was one defined.  It cound well be Lubuntu 13.04 uses it for the login screen.

Thanks again.

---

