---
title: "DosBox Resolution Problems"
date: 2014-01-04
forum: General Help
---

### Post by Shadius on 2014-01-04
Hi everyone,

I'm using DBGL to play Dune (not Dune 2), and the problem is whenever I play Dune in fullscreen mode, my Ubuntu desktop screen resolution gets changed to the resolution Dune goes into. How can I fix this? I have to log out of my desktop session to get the screen resolution back to normal, which is 1440x900. Any help is appreciated, thanks!

---

### Post by kostkon on 2014-01-04
Edit the profile for the game, click on the *Display* tab, set the *Output* to *openglnb* and the *Fullscreen Resolution* to the native for your monitor, if you can find it. If not (tbh, dbgl should be changed to ask randr for the available resolutions instead of presenting you with a list of hard coded resolutions), then set it to some random value (e.g. 1024x768) and press OK. After that you will need to locate the configuration file for the game in
```
~/.dbgl/profiles 
```
(whereas ~/ means your home folder; in your home folder, press CTRL+H to see hidden folders, or select *View -> Show Hidden Files* from the menu)
where it should be named after its position in your game list -for example if it is listed second in dbgl, its conf file should be *2.conf*- open it and change the line
from
```
[sdl]
fullresolution=1024x768
```
to
```
[sdl]
fullresolution=desktop
```

Also you might want to enable the* Aspect Correction* option, as it will not stretch the game to fit the resolution of your widescreen monitor, although you might like it that way, stretched.

Hope that helps.

---

### Post by Shadius on 2014-01-04
> **kostkon said:**
> Edit the profile for the game, click on the *Display* tab, set the *Output* to *openglnb* and the *Fullscreen Resolution* to the native for your monitor, if you can find it. If not (tbh, dbgl should be changed to ask randr for the available resolutions instead of presenting you with a list of hard coded resolutions), then set it to some random value (e.g. 1024x768) and press OK. After that you will need to locate the configuration file for the game in
```
~/.dbgl/profiles 
```
(whereas ~/ means your home folder; in your home folder, press CTRL+H to see hidden folders, or select *View -> Show Hidden Files* from the menu)
where it should be named after its position in your game list -for example if it is listed second in dbgl, its conf file should be *2.conf*- open it and change the line
from
```
[sdl]
fullresolution=1024x768
```
to
```
[sdl]
fullresolution=desktop
```

Also you might want to enable the* Aspect Correction* option, as it will not stretch the game to fit the resolution of your widescreen monitor, although you might like it that way, stretched.

Hope that helps.

Thanks for replying! For the *Fullscreen Resolution* drop down menu in DBGL, there's no option to select my native screen resolution of 1440x900. The highest option I have is 1280x1024. Is that okay?

---

### Post by kostkon on 2014-01-04
> **Shadius said:**
> Thanks for replying! For the *Fullscreen Resolution* drop down menu in DBGL, there's no option to select my native screen resolution of 1440x900. The highest option I have is 1280x1024. Is that okay?
Obviously, not; and by that, I mean you will need to edit its conf file, as I described in my previous post.

Also the numbering starts from 0 so the line
> where it should be named after its position in your game list -for example if it is listed second in dbgl, its conf file should be 2.conf- open it and change the line
needs to be changed to
> where it should be named after its position in your game list -for example if it is listed second in dbgl, its conf file should be 1.conf- open it and change the line

Hope that helps.

---

### Post by Shadius on 2014-01-04
Okay, got it. Thanks for the help.

---

### Post by kostkon on 2014-01-04
If you want that to apply globally to all your games, then you could create a new template (or edit one) and then change its resolution manually, like you did for your profile; templates should be in ~/.dbgl/templates.

---

### Post by Shadius on 2014-01-04
So that helped me make some progress, however, when I exit fullscreen mode from the game, my desktop's resolution changes to 1280x1024.

---

### Post by kostkon on 2014-01-04
> **Shadius said:**
> So that helped me make some progress, however, when I exit fullscreen mode from the game, my desktop's resolution changes to 1280x1024.
Do you mean you exit fullscreen mode while the game is running? And how?

---

### Post by Shadius on 2014-01-04
> **kostkon said:**
> Do you mean you exit fullscreen mode while the game is running? And how?

When I press **ALT+Enter** to exit fullscreen mode, and also when I completely exit the game.

---

### Post by kostkon on 2014-01-04
> **Shadius said:**
> When I press **ALT+Enter** to exit fullscreen mode, and also when I completely exit the game.
Hmm, you could try this:
first, make sure that you logout and log back in to revert to your default resolution, then run the game again and while you are there, check your current resolution by using your monitor controls (all monitors usually have an info option in their on-screen menu that displays your current res, refresh rate etc); is it really 1440x900 or 1280x1024?

---

### Post by Shadius on 2014-01-04
Everything seems to be working normal now. I can go into fullscreen mode and exit out of fullscreen mode while playing Dune without it effecting my desktop screen resolution. I created the template like you suggested. Thanks for your patience and helping me. Really apprecite it. Problem solved.

---

### Post by Shadius on 2014-01-04
> **kostkon said:**
> Hmm, you could try this:
first, make sure that you logout and log back in to revert to your default resolution, then run the game again and while you are there, check your current resolution by using your monitor controls (all monitors usually have an info option in their on-screen menu that displays your current res, refresh rate etc); is it really 1440x900 or 1280x1024?

The system froze up on me once just now and I had to shut down by holding the power button. Once I booted up again, I tried running the game a few times, and all is well. Thanks a bunch! I guess the restart helped.

---

### Post by kostkon on 2014-01-04
> **Shadius said:**
> The system froze up on me once just now and I had to shut down by holding the power button. Once I booted up again, I tried running the game a few times, and all is well. Thanks a bunch! I guess the restart helped.
Good news!
> **Shadius said:**
> Everything seems to be working normal now. I can go into fullscreen mode and exit out of fullscreen mode while playing Dune without it effecting my desktop screen resolution. I created the template like you suggested. Thanks for your patience and helping me. Really apprecite it. Problem solved.
My pleasure :)

---

