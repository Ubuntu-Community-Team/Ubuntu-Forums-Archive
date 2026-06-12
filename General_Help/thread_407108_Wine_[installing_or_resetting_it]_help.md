---
title: "Wine [installing or resetting it] help"
date: 2007-04-11
forum: General Help
---

### Post by Kizilbas on 2007-04-11
[img]http://images.apple.com/games/articles/2003/09/ageofmythology/images/dionysus.jpg[/img]

:KS :D :D :D 

How can I install wine from step to step properly, I couldn't manage to do it from Wine's website.

Pls help

thank you for you interest :)

---

### Post by Shay Stephens on 2007-04-11
Download the deb file here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Then open it to install with gdebi

Once installed, open the terminal and run:

```
winecfg
```

You can probably just accept the defaults and close the winecfg window as soon as it opens.

Then you have it installed and setup.

---

### Post by zvacet on 2007-04-12
Install it from synaptic.

---

### Post by Shay Stephens on 2007-04-12
> **zvacet said:**
> Install it from synaptic.
Does the dapper repository have the latest version?  Edgy and feisty do, but I am not sure if dapper does.

---

### Post by Kizilbas on 2007-04-12
Thank you very much I think it worked :), how can I access wine?
I wrote 'wine' in the terminal and i messy thing came up. How do I use wine to run msn messenger or install my webcam drivers from a CD?

---

### Post by Shay Stephens on 2007-04-12
Wine isn't a gui program, so in order to use it, you now only have to double click the windows program you want to run or install or perhaps right click on the program and choose "Open with wine".  If the program is on CD, insert the CD and double click on the setup.exe program or whatever the instructions say for installing the program.

Once installed, you may have an icon on the desktop that will run the program or perhaps in the applications menu.  But if not, then you will have to create your own or simply run the program from the terminal.  For example, if I want to run Photoshop 7, which I have installed, I run this command:
```
wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
``` 

Wine translates that into the linux directory location of where the program is actually stored on the computer, which in my case is:
/home/shay/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe

---

