---
title: "problem with ati + compiz"
date: 2008-06-24
forum: General Help
---

### Post by crackedparadigm on 2008-06-24
So my system was running compiz just fine on ubuntu 7.10. I upgraded to Hardy Heron and now my video is all screwed up. If it turn off visual effects, everything works fantastic. It's only when I turn on advanced visual that everything gets all messed up. 

I have included some screen shots to show what my problem is.

Anyone know how to help with this?

---

### Post by Forlong on 2008-06-24
What graphics chip and driver are you using?

In case you're not sure, you can use this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by crackedparadigm on 2008-06-24
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by novio8 on 2008-06-24
I also have problems with Ati, Compiz and Games
HP Compaq 6820, ATI Mobility Radeon X1350
ATI Accelerated graphics driver enabled in Hardware drivers
I tried a lot in yhe last week
I get the following responses

comiz-check
Gathering information about your system... 

 Distribution:          Ubuntu 8.04 
 Desktop environment:   GNOME 
 Graphics chip:         ATI Technologies Inc Unknown device 7196 
 Driver in use:         fglrx 
 Rendering method:      AIGLX 

compiz replace
root@laptio:/home/laptio# compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0


Checking if it's possible to run Compiz on your system... 

 Checking for texture_from_pixmap...               [ OK ] 
 Checking for non power of two support...          [ OK ] 
 Checking for composite extension...               [ OK ] 
 Checking for FBConfig...                          [ OK ] 
 Checking for hardware/setup problems...           [ OK ] 

Please Help
Mario

---

### Post by crackedparadigm on 2008-06-25
Bump

---

### Post by tornado89 on 2008-06-25
That's Because of XGL... On HARDY You Don't Need It Anymore. ATI Driver Works Great Without Composite Extensions...

remove the package xserver-xgl and restart

Hope It Works For You....

---

### Post by Rocket2DMn on 2008-06-25
First remove xserver-xgl
```
sudo apt-get remove --purge xserver-xgl
```
Then follow this thread for cards that use the open source "ati" driver (which includes your Radeon 7000) - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Forlong on 2008-06-25
Neither crackedparadigm nor novio8 have Xgl installed.

---

### Post by Rocket2DMn on 2008-06-25
I only mention it because some people upgrading from 7.10 have had problems because of it (myself included).  I'm not clear on the details of your script, so I couldn't gather that from quickly scanning the output.

---

### Post by crackedparadigm on 2008-07-29
bump

---

