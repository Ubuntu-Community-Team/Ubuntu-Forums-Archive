---
title: "Nvidia drivers went haywire."
date: 2007-11-01
forum: General Help
---

### Post by jake16424 on 2007-11-01
ohhkay,, so i installed most of my drivers all by my lonesome, ": thanks to all the help the last time i tried ubuntu. :" and now i rebooted,, well it was a while ago then i went to windows, now im back in buntu, however. on the splash screen " log on page"

it said that it couldn't determine my monitor or video card type, i thought to myself this is odd, as sense when i had just used 3D chess it worked just fine, except for the freezing up and crashing it ran like a charm,, 

thats when i rebooted.. now i installed my drivers AGAIN and, nothing new except the colors are a bit better,, so how do i access the controll pannel for my nvidia drivers?

and, how the hell do i get this back on track, it was going just fine, now its freaking out, i even modded a few things, to how i wanted them with some work and poking around and it came out great, now its poopy.. pweease help =-(

:confused::confused::confused:


ok so i just tried putting my display effects back to max or extra or whatever it's called. and it said unable to apply settings,, like no effects at all, and before the freeze up it worked just fine,,,,,,,,,, on high, and everything,, so i tried my launcher i made for my control panel for Ntune and nothing, doesn't work terminal came up with about 12190879087 errors, then shut down.. *sigh* linux officially hates me..

---

### Post by Crafty Kisses on 2007-11-01
Post the following output:
```
glxinfo
```

---

### Post by dabl on 2007-11-01
OK, so you have some kind of an Nvidia chip, some version of Ubuntu, and some kind of a motherboard and CPU/chipset, with some kind of LCD or CRT?

OK, here is _some kind_ of a solution.  :)

Downoad the Envy script installer, and use it.  You want the file

"envy_0.9.8-0ubuntu10_all.deb"

which is found about halfway down the web page here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

When the file is downloaded, right-click it and choose "Install with Gdebi" or whatever seems to do that for you.  When it is installed, open a console window and enter```
 sudo envy -t
``` and choose #1 "Install the Proprietary Driver"

Follow the instructions -- who knows, it might work!  :guitar:

---

### Post by jake16424 on 2007-11-01
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)
jake@jake-desktop:~$ 





dunno if that's what you wanted.. but i have a 

phillips 150S3 and i have

Epox motherboard 8dkah or something liek that, + a pro AGP port, with % PCI slots and

a Nvidia Nforce3 or 250gb chipset with a realtek AC850 sound chipset,,

and a Nvidia Geforce 5500FX graphics card,,

---

### Post by jake16424 on 2007-11-02
YEP  so i have reinstalled the packages as of last night " right now im at school " and so far no sucess it's goign to come down to me formatting the drive and reinstalling my drivers cause i am unexperienced and don't know what else todo. i uninstalled the python open GL thing's that i installed to get my 3D eccelorator working and it worked for 3d chess and then it crashed, i sense rebooted and WHAMMM all my settings keep resetting. it's as if my drivers are currupted or something. :mad::confused::confused::(

---

### Post by dabl on 2007-11-02
Just installing the Nvidia driver is not sufficient to enable GLX.

If you see the green and black Nvidia splash screen right before your login screen, then you DO have the Nvidia driver installed and running.  So, if that is the case, all you need to do is open a console window and enter:
```

sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

This will overwrite your xorg.conf file and add the GLX and compositing options.  When you restart the X server you'll be able to run compiz.

HTH  :)

---

### Post by jake16424 on 2007-11-02
> **dabl said:**
> Just installing the Nvidia driver is not sufficient to enable GLX.

If you see the green and black Nvidia splash screen right before your login screen, then you DO have the Nvidia driver installed and running.  So, if that is the case, all you need to do is open a console window and enter:
```

sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

This will overwrite your xorg.conf file and add the GLX and compositing options.  When you restart the X server you'll be able to run compiz.

HTH  :)

yeah, hense the thing where i said i got them installed, haha... owell.

i had them installed, i played 3D chess and my linux system froze, then i had to manually restart with the magnetic switch on the front of my tower. then i logged back in and while diong so, it said that i would have to set everything manually for my display cause linux couldn't determine the type of display i had, nore could it determine the graphics card.

THIS IS ALL AFTER IT HAD ALLREADY CONFIGURED ITSELF, SO IT DOESN'T MAKE SENSE

---

### Post by dabl on 2007-11-02
OK, let's do one problem at a time.

1. Regarding "frozen system", here is how to handle it in a way that won't bork up the filesystem:

[http://kubuntuforums.net/forums/index.php?topic=3088251.0](http://kubuntuforums.net/forums/index.php?topic=3088251.0)


2. Regarding the Nvidia driver -- if you installed Envy as instructed, then all you need to do is log in as a user, text mode is fine, and enter ```
sudo envy -t
```

and choose "install the proprietary driver" and it will be installed, and it will restart the X server for you.

---

### Post by jake16424 on 2007-11-02
> **dabl said:**
> OK, let's do one problem at a time.

1. Regarding "frozen system", here is how to handle it in a way that won't bork up the filesystem:

[http://kubuntuforums.net/forums/index.php?topic=3088251.0](http://kubuntuforums.net/forums/index.php?topic=3088251.0)


2. Regarding the Nvidia driver -- if you installed Envy as instructed, then all you need to do is log in as a user, text mode is fine, and enter ```
sudo envy -t
```

and choose "install the proprietary driver" and it will be installed, and it will restart the X server for you.


ok, well the python open GL or whatever i believe is what froze it up. so i have uninstalled it. if you wish, 

instant message me, on yahoo, jacob16424

and, yeah.. well should i get on ubuntu or stay with windows? its a dual boot system right now... 

and, sense i uninstalled that, it froze again, i installed something with like GTXget something or other,,, idk, i installed whatever 3D chess said was missing... :confused:

---

