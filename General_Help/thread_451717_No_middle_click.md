---
title: "No middle click?"
date: 2007-05-22
forum: General Help
---

### Post by Pizzarth on 2007-05-22
Hi, I'm running ubuntu studio but for some reason the middle-click doesn't work on the mouse. yes, the mouse is working fine, middle click does work. just not in here =/

I've been looking through the settings of the system and firefox and such, but havent found anything. Could someone tell me if middle click just doesn't work or if there's some way to fix it? 

thank you

---

### Post by LaRoza on 2007-05-22
Try clicking the left and right buttons at the same time or pressing the wheel, that may be counted as a middle click, but otherwise, it may not work in the app.

---

### Post by bapoumba on 2007-05-22
Please enter **about:config** in url, then go to **middlemouse.paste** line, and check it is set on **true**.

---

### Post by Pizzarth on 2007-05-22
>  	Please enter about:config in url, then go to middlemouse.paste line, and check it is set on true.

it is set to true.

>  	Try clicking the left and right buttons at the same time or pressing the wheel, that may be counted as a middle click, but otherwise, it may not work in the app.

pressing the mouse wheel is what i meant. Firefox and blender definitely support middleclick(new tabs and move around the object)

wow... well pressing both at once worked, but that's a little annoying. is there any other way that somebody knows of?

---

### Post by bapoumba on 2007-05-22
Which kernel are you using ?
Please check this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83571]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83571")

---

