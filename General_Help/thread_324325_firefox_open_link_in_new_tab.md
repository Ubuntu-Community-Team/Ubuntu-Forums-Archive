---
title: "firefox: open link in new tab?"
date: 2006-12-23
forum: General Help
---

### Post by Fittersman on 2006-12-23
is there anyway to make firefox open a link in a new tab, when you left click on it, instead of the scroll wheel?

basically what im asking is if you could swap the functions of the two for tab opening only but for everything else their functions would be normal.

---

### Post by aidanr on 2006-12-23
not that i know of, you can install the [tab mix plus]("https://addons.mozilla.org/firefox/1122/") extension which gives you a lot more control over the behavior of tabs, the nearest i can see to your idea is to force all links to open in a new tab

---

### Post by IcemanV9 on 2006-12-23
Hold down the CTRL key and left clink on link.

---

### Post by kerry_s on 2006-12-23
I'm justing looking at that now-> google>```
http://kb.mozillazine.org/About:config_Entries
```

---

### Post by ajgreeny on 2006-12-23
If you've got a three button mouse, middle click on the link and, voila, a new tab opens with the new page in it.

---

### Post by kerry_s on 2006-12-23
I'm justing looking at that now-> google>```
http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries
```

browser.link.open_newwindow     3
browser.link.open_newwindow.restriction   0

---

### Post by Fittersman on 2006-12-23
> **kerry_s said:**
> I'm justing looking at that now-> [http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries](http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries)

browser.link.open_newwindow     3
browser.link.open_newwindow.restriction   0

Do i type that in terminal?

---

### Post by NT4usB on 2006-12-23
> **Fittersman said:**
> Do i type that in terminal?

Open firefox.
Type the following in the location bar (that's where the [www.somewebsite.com](www.somewebsite.com) stuff goes):
```
about:config
```
There you can search and edit 
```
browser.link.open_newwindow 3
browser.link.open_newwindow.restriction 0
```
Trying to click the scroll wheel sux. I have a mouse that has buttons on the sides (Logitech mx310)
I reconfigured xorg.conf to use the thumb button as middle mouse. Much easier to click links and open tabs with the thumb than trying to click the scroll wheel without twitching.

Here's the relevant entry if you want to try it.
**_Be sure you back up xorg.conf before editing it and know how to restore it from a command line when X breaks and you have no GUI**_
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

```

ed: The ButtonMapping assigns functions to the mouse buttons. You can view them by typing:
```
xev
```
in a terminal and clicking in the window.

---

### Post by blackmh on 2006-12-23
Wheel click (middle button)

---

### Post by Fittersman on 2006-12-23
i know the wheel click makes it in a new tab, i was just wondering if i could change that because i would like the left click to open in a new tab and the wheel click to open in a new window... (kinda not that important but hey, might as well eh?)

another question about;

browser.link.open_newwindow 3
browser.link.open_newwindow.restriction 0

if i did that the way described above, will i need to have a thumb click? (i dont only right left and middle) and will it swap the buttons completely, because i dont want that, just the tab function to switch.

---

### Post by kerry_s on 2006-12-23
> **Fittersman said:**
> i know the wheel click makes it in a new tab, i was just wondering if i could change that because i would like the left click to open in a new tab and the wheel click to open in a new window... (kinda not that important but hey, might as well eh?)

another question about;

browser.link.open_newwindow 3
browser.link.open_newwindow.restriction 0

if i did that the way described above, will i need to have a thumb click? (i dont only right left and middle) and will it swap the buttons completely, because i dont want that, just the tab function to switch.


Nope your just changing what it would normally do, to what you want it to do, in this case open tabs instead of windows. Here's what i'm using, from the mozilla guide->

browser.link.open_newwindow  3
browser.link.open_newwindow.restriction  0
browser.search.openintab  true


If you want to go back to the original, just right click>reset

---

### Post by Fittersman on 2006-12-23
sweet, now is there a way to make the middle click open it in a new window?

---

### Post by NT4usB on 2006-12-23
> **Fittersman said:**
> i know the wheel click makes it in a new tab, i was just wondering if i could change that because i would like the left click to open in a new tab and the wheel click to open in a new window... (kinda not that important but hey, might as well eh?)

another question about;

browser.link.open_newwindow 3
browser.link.open_newwindow.restriction 0

if i did that the way described above, will i need to have a thumb click? (i dont only right left and middle) and will it swap the buttons completely, because i dont want that, just the tab function to switch.

No. Two separate things. Changing ```
about.config
``` only affects how Firefox acts.

Editing xorg.conf affects how your mouse acts on the entire system.

You can do one or the other or both...

---

### Post by kerry_s on 2006-12-23
I don't think so, you'll just have to use the right click.

---

