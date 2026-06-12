---
title: "[PARTIALLY SOLVED] problem with desktop background and Login image"
date: 2013-08-02
forum: General Help
---

### Post by julien-dal-col on 2013-08-02
hello,

I am running 13.04 and I'd like to change the desktop background.
I added a Jpg image and chose "scale" in order to display it correctly (not croped).
However, since the image is not as wide as the desktop, I get black bars on the side...
Since the background of the Jpg is white, I'd like to turn those black bars into white bars (to make them "invisible", sort of...)

I can pick a color for the desktop background (just next to where the format of the background image is defined), but this has no effect on the colors of the black bars... They remain black whatever color I pick...

This is obviously a "stupid" question, but I couldn't find a fix online.

Thank you very much in advance for your help.
Best,
-J-

ps. same thing with Png images

---

### Post by julien-dal-col on 2013-08-02
and now the same Jpg is used for the login window?!? I never set that up and I don't know how to set it back to the previous state...

Thoughts?

Best,
-J-

---

### Post by Frogs Hair on 2013-08-02
The login screen uses the same background as the desktop and it is intended to work that way . To make an image fit the desktop select fill or zoom . If the image is too small for the desktop it may be distorted when using fill or zoom . I'm am using a white background color along with my current wallpaper and it seems to work when scaling the image  if the pictures folder option is used in appearance preferences .
 
I don't get the same result if I use a image directly from the pictures folder unless background preferences selected when applying the image. When selecting set as desktop background image viewer displays the option to open background preferences.

---

### Post by julien-dal-col on 2013-08-02
Thank you very much for answering :)

> **Frogs Hair said:**
> The login screen uses the same background as the desktop and it is intended to work that way .
Well I don't like it since the image is not scaled and it looks ugly... There should be a way to set that differently (at least there was in older versions). We are talking free software here, right? ;)


 > **Frogs Hair said:**
> To make an image fit the desktop select fill or zoom . If the image is too small for the desktop it may be distorted when using fill or zoom .
Yes my image is too distorted (or croped) if I chose "fill" or "zoom". The Jpg is 1340x2008. the desktop is 1920x1200. The only realistic options are "scale" or "fit" that produce the same output (black bars on the sides).


 > **Frogs Hair said:**
> I'm am using a white background color along with my current wallpaper and it seems to work when scaling the image  if the pictures folder option is used in appearance preferences .
Do you mean that choosing the picture folder would change something? I tried putting my Jpg in the picture folder and then chose this file in the appearance tool -> same same...
 
> **Frogs Hair said:**
> I don't get the same result if I use a image directly from the pictures folder unless background preferences selected when applying the image. When selecting set as desktop background image viewer displays the option to open background preferences.
??? You lost me there... I don't understand what you mean.

Thank you very much again for your help
Best,
-J-

---

### Post by julien-dal-col on 2013-08-05
anyone?

---

### Post by Laobi on 2013-08-05
> **julien-dal-col said:**
> Yes my image is too distorted (or croped) if I chose "fill" or "zoom". **The Jpg is 1340x2008. the desktop is 1920x1200**. The only realistic options are "scale" or "fit" that produce the same output (black bars on the sides).

There is a huge difference in aspect ratio between that JPG image and your desktop, so it will be hard to get any satisfying results by just using scale, fill or zoom in the Background manager.
You will get better results if you take the image and scale/zoom it manually to 1920x1200 in a graphics editor like GIMP, and then use that new image as a background.

---

### Post by julien-dal-col on 2013-08-05
Thank you for answering :)

Well the result is very good using the scale or fit options. the only problem is that the "empty" part of the desktop (the part that is not "covered" by the jpg image) is black. I would like to set it up to a different color by using the corresponding option but, for some reason, whatever color I pick as background color the background is always black...

---

### Post by julien-dal-col on 2013-08-05
If I chose "colors & gradients" rather than an image as desktop background, the desktop is black. No mater what color I define as desktop background...
My best guess is that there is a bug somewhere preventing me from choosing anything else than black as desktop background...

---

### Post by julien-dal-col on 2013-08-05
[http://askubuntu.com/questions/288775/cannot-change-background-color-in-ubuntu-13-04](http://askubuntu.com/questions/288775/cannot-change-background-color-in-ubuntu-13-04)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center-unity/+bug/1173818](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center-unity/+bug/1173818)

---

### Post by julien-dal-col on 2013-08-06
I guess that means I am screwed until this bug is fixed, right?

---

### Post by mc4man on 2013-08-06
> **julien-dal-col said:**
> I guess that means I am screwed until this bug is fixed, right?
The bug about using a custom solid color or gradient has been fixed, it's in - 
 gnome-control-center-unity (1.3daily13.06.19~13.04-0ubuntu1) which still may be in raring-proposed. 

The orig. bug reporter re-opened that bug report on another small element that not in the orig. description & that hasn't been fixed. (He probably shouldn't have as its a separate bug, seen here - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center-unity/+bug/1194137](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center-unity/+bug/1194137)

So if you install gnome-control-center-unity (1.3daily13.06.19~13.04-0ubuntu1 you should be able to choose any custom solid color/gradient  But that's may not help, you'll need to try. 
(you may first have to reset the values for a solid color back to defaults after upgrading gnome-control-center-unity, I forget.

Otherwise as mentioned edit your image in gimp.

---

### Post by julien-dal-col on 2013-08-12
Thanks :D
I activated the repository for raring-proposed and among a bunch of other updates I have now:
gnome-control-center-unity 1.3daily13.06.19~13.04-0ubuntu1.

The background of the desktop can now be changed to a custom color and I thus could setup my nice image without any black bars on the sides :D

Now I still don't know how to revert the login screen image to the default one

Thanks again.
-J-

---

