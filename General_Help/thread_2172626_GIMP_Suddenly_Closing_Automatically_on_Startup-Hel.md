---
title: "GIMP Suddenly Closing Automatically on Startup-Help?"
date: 2013-09-05
forum: General Help
---

### Post by Rasa1111 on 2013-09-05
Hey guys, 
 I'm close to my wits end wih this seemingly new occurence. 

 Just yesterday I was using GIMP, no problems..
Today, I did some updates and installed a couple new indicators (psensors, my weather), Which I don't think would cause this-
and now everytime I try to open GIMP- It starts the splashscreen like normal..
and as soon as GIMP itself actually opens, Poof- It closes right out again- instantly. 

No matter how many times I try to restart it, or reboot my system,
I just cannot get GIMP to open. 
Everything acts just as it should, right until the GIMP window opens- then it immediately disappears and GIMP is no longer running.

Can anyone help me diagnose this? 
Anyone else had this happen to them that can steer me right? 

I'm kind of in need of GIMP at the moment, but I'm at a loss here. 

This is a pretty new install (few days old) of Ubuntu 13.04 - x64

I appreciate any and all help. Thank you. :)

---

### Post by ibjsb4 on 2013-09-05
Try opening it in terminal and see if you get any errors.

```
gimp
```

---

### Post by Rasa1111 on 2013-09-05
Hey there, 
Ok, did that... 
I got a lot of lines like
```
/home/android/.gimp-2.8/themes/Flat-Dark/gtkrc:1230: Unable to locate image file in pixmap_path: "trough.png"
/home/android/.gimp-2.8/themes/Flat-Dark/gtkrc:1234: Background image options specified without filename
```

and at the end I got
```
(script-fu:4781): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault

```

Which reminded me...
a couple days ago I installed a new "theme" in gimp to change the icons to a dark/mono type,
and it was working find until today, But that terminal output reminde dme of doing that,
So I just deleted the theme folder - tried again, and gimp opened! lol Wow, feel kinda dumb... :/ 
Thanks for the reply! , I don't know why that theme messed it up suddenly, but I dunno if I would have remembered without your post. O_o
:) Solved.  haha   
You rock.  :guitar: thanks a lot.

---

