---
title: "Pages not shown correctly in firefox"
date: 2006-11-18
forum: General Help
---

### Post by pgilmon on 2006-11-18
Hi all.

I was used to browse through pages that don't show correctly on Firefox. Or, at least, that's what I thought, because today I have tried Firefox under XP and all those pages are shown correctly. Why does this happen? I'm not only talking about pages with flash, which I think don't display correctly beacuse flash under linux is still in version 7. This happens also with pages that, at first sight, are very simple. In XP they are represented correctly, but not in ubuntu. Does this have to do with fonts or something? Is there any way of solving it?

Regarding the flash subject. I've noticed that some dinamic menus are drawn behind flash objects, so you can't click on their elements. (See webpages from the two major graphic cards manufacters). These pages are also shown correctly under Firefox+XP. Is is a flash issue or is there something to configure in Firefox to solve this?

Thanks for your time ;)

---

### Post by gosh on 2006-11-18
Which particular pages do you mean?
Do you have screenshots to illustrate your problem?

---

### Post by pgilmon on 2006-11-20
[http://www.lipasam.es/utiliza_puntos_limpios.php](http://www.lipasam.es/utiliza_puntos_limpios.php)
[http://www.nvidia.com/page/home.html](http://www.nvidia.com/page/home.html) (flash)
[http://ati.amd.com/](http://ati.amd.com/) (flash)

All those above are shown correctly in firefox under windows, but not under linux

---

### Post by gosh on 2006-11-20
> **pgilmon said:**
> [http://www.lipasam.es/utiliza_puntos_limpios.php](http://www.lipasam.es/utiliza_puntos_limpios.php)
[http://www.nvidia.com/page/home.html](http://www.nvidia.com/page/home.html) (flash)
[http://ati.amd.com/](http://ati.amd.com/) (flash)

All those above are shown correctly in firefox under windows, but not under linux

I have only trouble with the first one (see screenshot).
The other two are just fine. You have the flashplugin-nonfree installed?

---

### Post by pgilmon on 2006-11-20
I have edgy, Firefox 2.0 and flashplugin-nonfree installed through aptitude. I can't see the pages correctly: flash content stays over the deployed menus so you can't see them (or you can oonly see a little part of them).

When I installed flashplugin-nonfree aptitude automatically selected gsfonts-x11, which returned the following warnings during installation:

warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

---

### Post by Bretls on 2006-11-20
Same problem here. Also, on some webpages dhtml menus  will not load in the spot they were intended. So I am wondering if this is a problem with java or flash. Here is a page with dhtml menus that does not have flash on it. [Nj Transit]("http://www.njtransit.com/hp/hp_servlet.srv?hdnPageAction=HomePageTo")

---

### Post by gosh on 2006-11-20
Maybe I don't have this problem because I'm running Feisty with Flash 9 plug-in

---

### Post by Bretls on 2006-11-20
Just curious Gosh, what version of java do you have installed, I currently have 1.5.0_08. I have flash 9 installed and ver. 2.0 of firefox.

---

### Post by noynac on 2006-11-20
The second and third sites work fine for me. I'm running Edgy with Flash 7.0 r68 and Java Plug-in 1.5.0_08-b03.

---

### Post by PrinceArithon on 2006-11-20
There is a Flash Player 9 Beta for Ubuntu.  I use it and everything works.  I used to play on newgrounds.com all the time but the flash didn't work half the time.  As soon as I loaded in the Flash Player 9 it worked well.  Here is what you can try.


wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 


By plugging all of that into your terminal all should work out fine after you restart Firefox

---

### Post by pgilmon on 2006-11-20
I have updated to flash 9 beta by following the instructions provided by PrinceArithon. Now I can see flash 9 content, but I still have the same problem. I have installed also sun-java5-plugin, so I have version 1.5.0_08, but the result is just the same.

I also wanted to point out that there are other pages which don't have flash content and are not displayed correctly, but they can be seen with no problem using firefox 2.0 under windows (e.g.: [http://www.lipasam.es/utiliza_puntos_limpios.php](http://www.lipasam.es/utiliza_puntos_limpios.php))

---

### Post by PrinceArithon on 2006-11-20
AH yes I see what you are saying, gives me the same problem.  I don't know what to say really.  It could be just because of how Linux allows the browser to view the code.  The thing is, poor code is not something Linux wants to see.  Also it could be because the site was made for a lower resolution...again if that is the case, and it's not working in a higher resolution then it's still poor coding again.

---

### Post by gosh on 2006-11-20
> **Bretls said:**
> Just curious Gosh, what version of java do you have installed, I currently have 1.5.0_08. I have flash 9 installed and ver. 2.0 of firefox.

sun-java-jre 1.5.0-08-0ubuntu1 (feisty)
flashplugin-nonfree 9.0.21.55.3ubuntu1 (feisty)

---

### Post by doobit on 2006-11-20
This is a problem with the non-Windbloze versions of Flash. I have the same problem with the plugin in FireFox for OSX on a Mac.

---

