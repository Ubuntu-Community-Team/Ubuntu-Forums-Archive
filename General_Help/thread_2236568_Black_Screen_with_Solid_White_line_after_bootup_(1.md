---
title: "Black Screen with Solid White line after bootup (14.04)"
date: 2014-07-27
forum: General Help
---

### Post by TheVolamoot on 2014-07-27
[COLOR=#000000]I recently got around to upgrading an old secondary server from the 12.04 to the more recent LTS of 14.04, with 12.04 there was the standard Unity interface that would show after bootup but after the upgrade things seem to be going a little wonky. I know the server boots for the most part correctly as SSH works perfect and all server apps continue to work properly however the Unity desktop never shows and only a black screen with solid white line appears. I have tried troubleshooting and i'm unable to determine what is failing during bootup. [/COLOR]

[COLOR=#000000]During the bootup process the screen goes from the regular 5 dot ubuntu plymouth splash screen to what appears to be a verbose bootup then back to the ubuntu slash screen, where it completes bootup and goes to the black screen with white line. [/COLOR]

[COLOR=#000000]Any Help resolving this issue would be greatly appreciated.[/COLOR]

---

### Post by Bashing-om on 2014-07-27
alexander.springer; Hi !

A server with a GUI (unity) .. Did you install the "ubuntu-desktop" ? 
I Surmise that with that GUI inplace, you were running a proprietary driver, and in the upgrade process the driver got broke.

Might I suggest you remove the -probable- proprietary graphics driver and (RE-)install a graphics driver ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by TheVolamoot on 2014-07-27
Thanks for the reply,
I have already tried reinstalling the graphical drivers, but i havn't tried reinstalling the Ubuntu-Desktop. I think I will try doing the ubuntu-desktop reinstall. Thanks for the suggestion I'll update this post with the results.

UPDATE: So during the attempted reinstall for the ubuntu-desktop I found that a package by the name of "checkbox-gui" was missing. However during my attempt to install the checkbox-gui i found that all of its dependencies are unavailable from the repository and as such wont install. Not quite sure where to go from here... I'm wondering if it would be easier to just do a new install from the live cd while saving my previous files and settings.

---

### Post by TheVolamoot on 2014-07-27
Okay so after some more digging I found my issue has already been listed as a bug since 13.10 and such the only solution is to run a repair install from dvd.
[http://ubuntuforums.org/showthread.php?t=2236294](http://ubuntuforums.org/showthread.php?t=2236294)

hopefully this issue is fixed in the future but as it doesn't appear very often i can see why its still floating around. Thanks for you help Bashing-Om.

---

### Post by Bashing-om on 2014-07-27
alexander.springer; Great !

Glad ya got it all sorted out, up and running .
That is what makes this forum great - finding those work-a-rounds - when out-of-the-box does not fit.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

