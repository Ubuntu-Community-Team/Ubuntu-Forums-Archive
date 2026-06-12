---
title: "How to run Dream Aquarium on Ubuntu (Or any other) Linux"
date: 2007-02-23
forum: General Help
---

### Post by darkmaster on 2007-02-23
Hi everyone! I just wanted to tell you people that since there's no decent 3D aquarium screensaver for Linux, I managed to have the fantastic Dream Aquarium (For WIndows only) working under Linux! Not only: look at this videos and you'll see just some little trick you can do by using Dream Aquarium togeter with Beryl :)

[http://www.youtube.com/watch?v=pcdCiy4p63U](http://www.youtube.com/watch?v=pcdCiy4p63U) 
[http://www.youtube.com/watch?v=RNrTIrRKEYs](http://www.youtube.com/watch?v=RNrTIrRKEYs)

Go rate my videos on youtube! Eyecandy on the n power. I also created a Step by Step Tutorial on how to have Dream Aqaurium running perfectly under Linux. You can find the Tutorial here:

[http://dreamaquarium.com/forum/viewtopic.php?p=5226#5226](http://dreamaquarium.com/forum/viewtopic.php?p=5226#5226)

Of course, follow the instructions and download the DC Demo from:

[http://www.dreamaquarium.com](http://www.dreamaquarium.com)

It all started from a Topic I opened on the Beryl Forum, here's the original link:

[http://forum.beryl-project.org/viewtopic.php?f=40&t=3642&st=0&sk=t&sd=a](http://forum.beryl-project.org/viewtopic.php?f=40&t=3642&st=0&sk=t&sd=a)

If you like all of this, please, feel free to try it out yourself, if you don't find Wine is disgusting :) (naturally, I absolutelly love Wine :lolflag: )
Hope this can be of any help and appreciation for anyone! I also noticed that my video is now on [www.ubuntuvideo.com](www.ubuntuvideo.com) in the main page :)

---

### Post by highneko on 2007-02-24
Cant get crossover to work. Tried winecfg and regedit. Wine won't let me use it either. Just the screensaver alone would be nice. After the install when I press start screensaver it says this:
```
[: 221: ==: unexpected operator
[: 221: ==: unexpected operator
[: 221: ==: unexpected operator
[: 221: ==: unexpected operator
err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\Dream Aquarium\\Dream_Aquarium.scr") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Dream Aquarium\\Dream_Aquarium.scr" failed, status c0000135
err:rundll32:main Unable to load L"desk.cpl"

```I read the guide and the troubleshooting stuff too. Great videos btw. Rated 5/5. n_n

---

### Post by revertex on 2007-03-04
i can't get it to install using wine, but run like a champ.
with some voodoo i got it to work, just need to install it in windoze then copy to wine folder.
for those poeple that don't have crossover, wine is enough to run.

i recomend install in a separate wine folder, like crossover bootle, there is a how-to here.

[http://frankscorner.org/index.php?p=wineprefix](http://frankscorner.org/index.php?p=wineprefix)

then run ```
[FONT=verdana][SIZE=2]**WINEPREFIX="~/path-to-dreamaquarium-folder" winecfg**[/SIZE][/FONT]
``` and uncheck "emulate virtual desktop" in graphics tab, according to darkmaster tutorial.

this way you can use it full screen without a need to run all your wine apps in a virtual desktop.

don't forget to write a bash script to lauch it, something like:

```
#!/bin/bash
cd "$HOME/[FONT=verdana][SIZE=2]**path-to-dreamaquarium-folder**[/SIZE][/FONT]/drive_c/Program Files/Dream Aquarium"
WINEPREFIX="~/[FONT=verdana][SIZE=2]**path-to-dreamaquarium-folder**[/SIZE][/FONT]" wine Dream_Aquarium.scr
```
 
my next step is to discover how to configure it as an animated wallpaper with xwinwrap.

thank you darkmaster.

---

### Post by revertex on 2007-03-04
@[highneko]("http://www.ubuntuforums.org/member.php?u=175489")

take a look here [http://www.dreamaquarium.com/download_w2k.html](http://www.dreamaquarium.com/download_w2k.html)

you need gdiplus.dll

---

### Post by darkmaster on 2007-04-12
> **revertex said:**
> 
my next step is to discover how to configure it as an animated wallpaper with xwinwrap.

thank you darkmaster.

Thanks to you for helping with instructions on Wine installation :)
And yes, to be able to use it as a wallpaper using xwinwrap would be my dream too. I'm trying to do it with no success :(

---

### Post by darkmaster on 2007-04-12
> **revertex said:**
> @[highneko]("http://www.ubuntuforums.org/member.php?u=175489")

take a look here [http://www.dreamaquarium.com/download_w2k.html](http://www.dreamaquarium.com/download_w2k.html)

you need gdiplus.dll

Yes, exactly. I only noticed too lae that people needed that driver. I also updated my How-to:
[http://www.dreamaquarium.com/forum/viewtopic.php?t=648]("http://www.dreamaquarium.com/forum/viewtopic.php?t=648")

Now I also included, available for download, a preconfigured Crossover Bottle with Dream Aquarium allready installed in it! :D
You only have to install the bottle with Crossover, run regedit and edit your screen resolution as I explain in my Tutorial. Have a nice Dream Aquarium ;)

P.S.: The Crossover Bottle contains the latest trial version of DA. I created it according to Spiral Monkey's (The authors of Dream Aquarium) permission, so you don't violate any law. They'll soon add my Crossover Bottle to the official Linux download page of Dream Aqaurium :)
Sorry for not realizing before about the dll...

---

### Post by darkmaster on 2007-04-20
Nice update, please, visit my blog here:
[http://thedarkmaster.wordpress.com/2007/02/27/the-beryl-dream-aquarium/](http://thedarkmaster.wordpress.com/2007/02/27/the-beryl-dream-aquarium/)
and read the comments! Maybe we'll have DA working as a background very soon!!!

---

### Post by soulbreak on 2007-09-11
It appeared to install in wine fine, I can access the screensaver config to change the resolution etc.  but when I try to actually run the .scr with wine ubuntu just crashes and immediately restarts into the login screen.

---

### Post by darkmaster on 2007-09-11
> **soulbreak said:**
> It appeared to install in wine fine, I can access the screensaver config to change the resolution etc.  but when I try to actually run the .scr with wine ubuntu just crashes and immediately restarts into the login screen.

Are you sure you downloaded and installed gdiplus?

---

### Post by soulbreak on 2007-09-11
I put gdiplus in the wine windows/system32 folder,  there is a gdi32.dll in that folder though, should I remove that?

---

### Post by darkmaster on 2007-09-11
> **soulbreak said:**
> I put gdiplus in the wine windows/system32 folder,  there is a gdi32.dll in that folder though, should I remove that?

Well, that's weird, sorry but I don't know how to solve your problem. Except... once another user had this same problem but he didn't have 3D support on his linux box. Do you have a 3D card and does it work properly with others 3D apps?

---

### Post by vapore0n on 2007-09-11
same, but my video card (intel) sucks
direct rendering = no

---

### Post by darkmaster on 2007-09-11
> **vapore0n said:**
> same, but my video card (intel) sucks
direct rendering = no

Well, without direct rendering DA won't work at all, sorry :(

---

### Post by soulbreak on 2007-09-11
I can't remember the exact model or command to display hardware info right now but I think mine is an intel too.  Other 3d apps run without crashing (Compiz, AWN) but I did notice the screensaver doesn't let you use opengl to render so I guess that is the prob.  Couldn't I use the same method you have for any aquarium screensaver though?  In my case, one that supports opengl?

---

### Post by durand on 2007-09-24
> **soulbreak said:**
> I can't remember the exact model or command to display hardware info right now but I think mine is an intel too.  Other 3d apps run without crashing (Compiz, AWN) but I did notice the screensaver doesn't let you use opengl to render so I guess that is the prob.  Couldn't I use the same method you have for any aquarium screensaver though?  In my case, one that supports opengl?

Not sure about intel but with nvidia, you need to update to the latest drivers to run opengl apps and compiz at the same time.

---

### Post by erisianmonkey on 2007-11-25
Hey Darkmaster,

I just posted a little bit ago on Alan's forum. I was wondering if you had any idea how to do the wallpaper thing now that beryl has merged with compiz? That, and I'm looking for a way to have the screensaver control in gnome pull up DA in wine. I haven't hit on the right keywords to pull up even a starter clue yet, but hopefully I'll get there.

---

### Post by darkmaster on 2007-11-25
> **erisianmonkey said:**
> Hey Darkmaster,

I just posted a little bit ago on Alan's forum. I was wondering if you had any idea how to do the wallpaper thing now that beryl has merged with compiz? That, and I'm looking for a way to have the screensaver control in gnome pull up DA in wine. I haven't hit on the right keywords to pull up even a starter clue yet, but hopefully I'll get there.

Hello! Since when Beryl remerged with Compiz in the new Fusion, I never tried it out. In any case you should refer to the author of the application able to have Wine apps run as wallpapers in Beryl. In my article you'll find every detail about the author, you should ask him to fix / upgrade his application :)

It would really be interesting.
If you manager to find a solution please ping back on me and I'll post it on my blog :)

---

