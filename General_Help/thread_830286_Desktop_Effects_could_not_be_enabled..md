---
title: "Desktop Effects could not be enabled."
date: 2008-06-15
forum: General Help
---

### Post by mrmustardman on 2008-06-15
I am running Ubuntu 8.04, and when I try to enable the desktop effects, it gives the error "Desktop Effects could not be enabled." I had this problem before, and I had solved it. But I dont remember what I did, it was a long time ago. I think I had to do something with my xorg file, like reset it, or add something. I do not remember. I am running Ati Radeon Mobility 9000. I remember that last time I installed Ubuntu, it was an earlier version, and I was able to turn the effects on right after I installed it, have the effects gotten too good for my card, so it wont enable?

Sorry, i just read the below topic on this haha, i feel dumb.

---

### Post by argail1980 on 2008-06-15
have a look at [compiz-check]("http://forlong.blogage.de/article/pages/Compiz-Check")

you can also try in a terminal

```
compiz --replace
```

This gives you more usable error messages than "could not be enabled"

---

### Post by Reu on 2008-06-15
I have a similar problem. Recently I installed Compiz fusion and when I tried the compiz --replace comand it give me the following error:
"reu@reu-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
"
you can help me with this that would be great. I am fairly new to linux
If

---

### Post by jp734 on 2008-06-15
Have you tried the compiz-check as mentioned above? If you have and still getting error, make sure you are using the right driver for your video card not the VESA driver. Desktop Effects doesn't work with VESA driver.

You can also check my xorg.conf file which is in ascii text format and compare. Maybe you will find what's missing on yours: [http://ubuntuforums.org/attachment.php?attachmentid=71044&d=1211414152](http://ubuntuforums.org/attachment.php?attachmentid=71044&d=1211414152)

Look under:
Section ServerFlag
Section DRI
Section Modules

I also remember that I had to install MESA-DRI using Synaptic Package Manager to get mine to work.

Still need help, please post you xorg.conf file

---

### Post by Rocket2DMn on 2008-06-15
Here is the workaround for ATI cards using the open source drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Enjoy :)

---

### Post by argail1980 on 2008-06-16
but this look like it already works (almost)..

> Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

start the gconf-editor (hit Alt+F2 and enter gconf-editor)

and look for this key:

> /apps/compiz/plugins/scale/allscreens/options/initiate_edge


try to give it an empty value or to delete it (the latter is NOT recommended by me). reading this error message, that should already do the trick

---

