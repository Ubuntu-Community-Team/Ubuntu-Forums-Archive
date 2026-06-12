---
title: "How can I gt a dock like a mac?"
date: 2008-06-14
forum: General Help
---

### Post by the lemming on 2008-06-14
I tried installing AWN but absolutely nothing happened and I mean nothing except for a little icon that pops up at the top of my screen.

---

### Post by fooman on 2008-06-14
you need to turn on the "visual effects" (compiz/fusion) in order to use AWN.

go to system > preferences > appearance > visual effects tab

put a tick in the box next to "extra" ...then try AWN.

---

### Post by the lemming on 2008-06-14
[QUOTE=fooman;5187132]you need to turn on the "visual effects" (compiz/fusion) in order to use AWN.

go to system > preferences > appearance > visual effects tab

put a tick in the box next to "extra" ...then try AWN.[/QUOTE

I've tried that but nothing happens.  All I get is a split second view of a small gray box but it does not stay there ling enough fro me to see much.

---

### Post by fooman on 2008-06-14
are your video drivers installed?

are the other visual effects working (cube, wobbly windows, etc...)? 

try running AWN from a terminal and see what errors pop up:

```
avant-window-navigator
```

---

### Post by the lemming on 2008-06-14
> **fooman said:**
> are your video drivers installed?

are the other visual effects working (cube, wobbly windows, etc...)? 

try running AWN from a terminal and see what errors pop up:

```
avant-window-navigator
```



Weird.  I'm no expert of the terminal but when I typed avant-window-navigator it seemed to work because I got two icons, one for the terminal and one for Firefox which was running.  However when I closed the Terminal then the icons vanished.


I'm running Ubuntu on a laptop with no propriety drives.

---

### Post by the lemming on 2008-06-14
After my last post I gt something new.  When I click the AWN icon to launch it I get an AWN Manager box.

Any suggestions on how to use it so that I can get it up and running?

Cheers

---

### Post by Genius314 on 2008-06-14
> Weird. I'm no expert of the terminal but when I typed avant-window-navigator it seemed to work because I got two icons, one for the terminal and one for Firefox which was running. However when I closed the Terminal then the icons vanished.


Yeah. When you run a program from the terminal, it will close as soon as you close the terminal.
Try pressing Alt-F2 and then typing avant-window-navigator.

And to get it to load on login, go to System>Preferences>Sessions. Click "Add," give it a name like AWN or something (doesn't matter, really) and put avant-window-navigator as the command.

---

### Post by the lemming on 2008-06-14
OK

I can now get it to be up and runing when I start my computer but all I get is a small empty box at the bottom of the screen however when I run an application like Firefox then the small box expands and fills with the Firefox icon.  If I run another application the box expands again to show the new icon.  Not much help if I intend to use this new feature to start applications.

I'm assuming that I have to add a Launcher or something like that?

I really would appreciate some advice on browsing for the comands that will launch stuff.  Please be patient with me as I'm from a windows environment and as such I would rather go down the road of graphical input rather than text input.

Any suggestions how I can fill the box with icons off applications much like those that are displayed at the top of my monitor in the top panel?

Cheers

---

### Post by Genius314 on 2008-06-14
To add launchers, just right click on a blank part of the dock, and click "Preferences."
In the list on the left ("General, Applets, Launchers, Themes"), click on Launchers. Click add, and enter some details... name and description shouldn't matter too much, as long as you can remember what they are.
For command, you need the command that runs that program (e.g. "firefox" will run Firefox).

If you want to find more commands, right-click on the main menu on your panel ("Application, Places, System"), and click "edit menus." Find the program you want, right-click and select "properties." Here you'll find the command you need to run the program. Just copy and paste it into the launcher properties for AWN.

Hope that makes sense. :)

---

### Post by the lemming on 2008-06-16
> **Genius314 said:**
> To add launchers, just right click on a blank part of the dock, and click "Preferences."
In the list on the left ("General, Applets, Launchers, Themes"), click on Launchers. Click add, and enter some details... name and description shouldn't matter too much, as long as you can remember what they are.
For command, you need the command that runs that program (e.g. "firefox" will run Firefox).

If you want to find more commands, right-click on the main menu on your panel ("Application, Places, System"), and click "edit menus." Find the program you want, right-click and select "properties." Here you'll find the command you need to run the program. Just copy and paste it into the launcher properties for AWN.

Hope that makes sense. :)


I'm very sorry but my limited knowledge of Ubuntu/linux is too limited to follow your brief description of what to do.  Once I click file system I am presented with a huge list of folders that I do not have a clue are or what should be in them.

Would it be possible for somebody to explain how I find the applications that I need to add to the launcher?

Cheers

---

### Post by the lemming on 2008-06-17
BUMP.

Anybody,please?

Cheers

---

### Post by brethren on 2008-06-17
have you tried cairo dock? it's dead easy to set up:)

---

### Post by ladr0n on 2008-06-17
From the application menu, right click the applications you want and select "add to desktop".  Then right click on the new icon and select "properties".  Click the "Launcher" tab.  Copy and paste the "Command" field you see here to the "Command" field in AWN's add launcher dialog.  You can fill out the other fields if you want, but they aren't necessary. Restart AWN and you're ready to go.

---

### Post by the lemming on 2008-06-18
After a bit of tinkering I have managed to get an icon to appear in the small Grey box at the bottom of my scree.  

I have managed to get a small icon that will allow me to start up Firefox.  The only problem is that the icon is not the Firefox logo.  It is actally a little applet launcher with a spring under it.  However when I launch Firefox from the upper panel then Firefox starts and a Firefox icon appears in the AWM Grey box at the bottom of the screen.

Obviously I am doing something wrong but I don't know what.  Any suggestions would be most appreciated.

Cheers

---

### Post by jonathan.gardner04 on 2008-06-18
Awn will work like the Mac doc it just takes a bit of work to get it there.  Check out this [link]("http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/") and skip down to the section about adding apps to AWN.

---

### Post by Ryklou on 2008-06-18
try simdock (it is just like awn, if you do not enable desktop effects.)

go termanal 
```
<apps><accessories><termanal>
```
then type the following.
```
sudo apt-get simdock
```

when done d/l it go 
```
<apps><accessories><simdock>
```

Icon will be red horseshoe magnet

---

### Post by the lemming on 2008-06-18
Top bananna

Thank you for that link and the advice.  A hell of a lot better

Cheers

---

