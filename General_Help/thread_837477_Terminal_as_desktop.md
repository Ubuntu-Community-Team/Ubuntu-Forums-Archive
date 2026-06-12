---
title: "Terminal as desktop"
date: 2008-06-22
forum: General Help
---

### Post by ojthejuice on 2008-06-22
will someone please tell me how to put a terminal in my desktop. I've tried the following direction but they did not work, 


[http://www.linuxhaxor.net/2008/05/01/configuring-linux-terminal-to-work-as-a-transparent-wallpaper-part-2/](http://www.linuxhaxor.net/2008/05/01/configuring-linux-terminal-to-work-as-a-transparent-wallpaper-part-2/)

---

### Post by Doji on 2008-06-25
The guide your following typed in the command to start the gnome terminal incorrectly. Use this instead:

```
gnome-terminal --window-with-profile=DesktopConsole
```

(it goes in System > Preferences > Sessions, like indicated in the guide)

Also make sure that you chose - dynamically set title "isn't displayed" - under the "Title and Command" tab of the gnome terminal profile options.

If you're using Compiz you shouldn't need to use devilspie. Just respond to this and I'll tell you how to set up the terminal under Compiz.

---

### Post by dexter.deepak on 2008-06-25
doji..even i would like to know this setting on compiz..

---

### Post by Doji on 2008-06-25
Ok, so this is how to set up a desktop terminal using Compiz.

First, make sure you have CCSM installed

```
sudo apt-get install compizconfig-settings-manager
```

Start up the gnome terminal. Go to File > New Profile. Type in DesktopConsole and hit Create.

In the General tab uncheck "Show menubar by default".

In the Title and Command tab set Dynamically-set title to "Isn't displayed".

In the Effects tab check Transparent Background and move the slider to "None".

In the Scrolling tab set the scrollbar to "Disabled".

In the colors tab, it might be helpful to change the text color to something that'll be visible on your wallpaper.

Close the window.



Go to System > Preferences > Advanced Desktop Effects Settings.

Scroll down and click on "Window Decoration". In the field labeled "Decoration Windows" replace "any" with

```
!title=DesktopConsole
```

Go back, scroll down, and click on "Window Rules". Make sure it's enabled, and next to "skip taskbar", "skip pager", "below", and "sticky" type

```
title=DesktopConsole
```

Click on the "Size Rules" tab, hit new, type in title=DesktopConsole, and choose a suitable size for your terminal.

Go back and click on "Place Windows". Make sure it's enabled and click on the "Fixed Window Placement" tab. Hit new, type in title=DesktopConsole, and decide where on the desktop you want the terminal. x=5 and y=30 should be good for most people.

Close CCSM.



Press alt+F2 and type in 

```
gnome-terminal --window-with-profile=DesktopConsole
```

Your terminal should now be on your desktop. Now it's just a matter of getting it to start up automatically.

Go to System > Preferences > Sessions. Press "Add". Name it whatever you want and for the command type

```
gnome-terminal --window-with-profile=DesktopConsole
```

Enjoy.

---

### Post by kingpin393 on 2008-10-18
Thanks for the tutorial Doji,  it works great but when I startup it doesn't put the consol in the right spot it puts it at position 0,0.

I want it to be on the right-hand slide of the screen...

Anyone know how I can fix this?

---

### Post by loomsen on 2008-10-18
You can grab the position of a window by typing xwininfo and klicking on any window.

And you may append --geometry= X-GEOMETRY to the command above.

for instance, mine is:
```

gnome-terminal --title=deskterm --geometry=75x30+10+65 --window-with-profile=DesktopTerminal

```

starting it with 10 pixels space to the left edge and 65 pixel space to the top edge.

The first part of the geometry secification depends on the application. It's either in digits or pixels.

The gnome terminal's default is digits, which is reasonable for a terminal...

*hint*

Open up a terminal, placa it where you want it to be, then run xwininfo and chose the window. Look at the screenshot:
[[img]http://img505.imageshack.us/img505/8128/screenshot51mt0.th.png[/img]](http://img505.imageshack.us/img505/8128/screenshot51mt0.png)

so, in this case, you would append --geometry=80x34-6+99 to have a window launched there.
Then launch a window with specifications to make it transparent, and BAM

---

### Post by Zachx65 on 2008-11-02
Any way to have this one just one workspace?

---

### Post by loomsen on 2008-11-02
[Check this out](http://georgia.ubuntuforums.com/showthread.php?p=6061456)

---

### Post by daximus on 2008-11-03
These instructions work great, thanks!

I did find one small problem, though... If you use the "show desktop" button to minimize everything, the "desktop terminal" window goes down, too, and there's no way to get it back without hitting the button again (which of course brings everything else back up).  Also, if this term window has focus, and you hit alt-space then minimize, there's no way to get back to it at all.

Is there also a way to prevent "show desktop" from minimizing this window?

---

### Post by justacreep on 2008-11-03
Why dont you just install Tilda then add it to startup?

---

### Post by daximus on 2008-11-05
Tilda has no positioning options =)

---

