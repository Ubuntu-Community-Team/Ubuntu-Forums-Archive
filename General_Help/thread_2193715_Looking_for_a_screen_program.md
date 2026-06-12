---
title: "Looking for a screen program"
date: 2013-12-14
forum: General Help
---

### Post by Mark de J on 2013-12-14
A boo,

Is there a program to make screenshots of a window and upload it automatic.

In windows it is prntscr, is there something for it on Linux?

---

### Post by r-senior on 2013-12-14
There is the Screenshot application, which you can find by searching in the Dash for 'Screenshot'.

You can get a quick whole-screen screenshot by pressing the 'Print Screen' key on your keyboard.

What do you mean by upload automatically?

---

### Post by Mark de J on 2013-12-14
On the program PrntScr you can upload the images direct after making a screenshot.

---

### Post by tgalati4 on 2013-12-14
Alt-PrintScr will make a screenshot of just the active window.  There may be some settings to alter the behavior.  Where does the Windows PrintScreen program upload the images to?

There is also *shutter*.  [http://askubuntu.com/questions/140833/how-to-take-a-screenshot](http://askubuntu.com/questions/140833/how-to-take-a-screenshot)

With a script, you could take a screenshot and save it to a directory (say Flickr_Upload) and have some flickr utilities automatically upload it.

---

### Post by Mark de J on 2013-12-14
To that server?

[http://prntscr.com/2505sf](http://prntscr.com/2505sf)

---

### Post by tgalati4 on 2013-12-14
According to the terms-of-service, that site uses imageshack to host the images.  There is a utility that you can use:

tgalati4@Mint14-Extensa ~ $ apt-cache search imageshack
imageshack-uploader - a image and video upload utility for the ImageShack hosting service
imageshack-uploader-common - a image and video upload utility - common files
kipi-plugins - image manipulation/handling plugins for KIPI aware programs

---

### Post by Mark de J on 2013-12-15
> **tgalati4 said:**
> According to the terms-of-service, that site uses imageshack to host the images.  There is a utility that you can use:

tgalati4@Mint14-Extensa ~ $ apt-cache search imageshack
imageshack-uploader - a image and video upload utility for the ImageShack hosting service
imageshack-uploader-common - a image and video upload utility - common files
kipi-plugins - image manipulation/handling plugins for KIPI aware programs
OK, and how do I get it? Software center?

---

### Post by jimmyh1972 on 2013-12-17
"[COLOR=#000000]*According to the terms-of-service, that site uses imageshack to host the images. There is a utility that you can use:*[/COLOR]

[COLOR=#000000]*tgalati4@Mint14-Extensa ~ $ apt-cache search imageshack*[/COLOR]
[COLOR=#000000]*imageshack-uploader - a image and video upload utility for the ImageShack hosting service*[/COLOR]
[COLOR=#000000]*imageshack-uploader-common - a image and video upload utility - common files*[/COLOR]
[COLOR=#000000][I]kipi-plugins - image manipulation/handling plugins for KIPI aware programs"

sudo apt-get install each app...[/I][/COLOR]

---

