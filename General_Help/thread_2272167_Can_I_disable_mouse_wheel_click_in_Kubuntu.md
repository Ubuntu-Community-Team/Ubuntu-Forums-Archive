---
title: "Can I disable mouse wheel click in Kubuntu?"
date: 2015-04-04
forum: General Help
---

### Post by scottbomb on 2015-04-04
I use the mouse wheel to scroll up and down on web pages, but occasionally I apply a little too much pressure and I end up pressing down on it. If there happens to be a hyperlink underneath, Firefox does it's duty and spawns a new tab.

Is there a way to disable this behavior? I do still want to use the middle wheel but I'd like to be able to disable it's use as a mouse button. I can't find mouse settings for this. I searched to see if anyone else had the same issue and all I can find is people trying to disable "click-paste", which is NOT the problem here.

BTW, the mouse has a few other buttons too, but they aren't configurable at all.

Any idea?

---

### Post by Holger_Gehrke on 2015-04-04
You could try your luck in the "about:config" page in firefox. There's several option there whose name contains "middleclick" or "middlemouse", but I couldn't find the right combination of options to eliminate this behaviour.

BTW: X assumes a mouse has at most 5 button (left, middle, right, wheel up and wheel down). If you have more, you have to tell X about them in an "xorg.conf" file. X has become very good at detecting the right settings for most stuff, so you probably don't have an "xorg.conf". There's a manual page for this file 'man 5 xorg.conf'.

---

### Post by ajgreeny on 2015-04-04
> **Holger_Gehrke said:**
> X assumes a mouse has at most 5 button (left, middle, right, wheel up and wheel down). If you have more, you have to tell X about them in an "xorg.conf" file. X has become very good at detecting the right settings for most stuff, so you probably don't have an "xorg.conf". There's a manual page for this file 'man 5 xorg.conf'.
I am not sure that is always the case any more.

I have a mouse with the usual left, right, middle, scroll up and scroll down, which all work as expected; I also have two extra buttons, one on each side, both of which work fine in web-browsers and file managers to move backwards and forwards.  I have not added anything to my system to get them working and I have no xorg.conf file any more, so the system obviously managed to configure those extra buttons at installation of the system.

Incidentally, the same was true of the media and all the extra buttons on my keyboard for mute, volume up and down, next or previous track in playlist, sleep/suspend, audioplayer (gmusicbrowser in Xubuntu), web-browser (whatever the set default is), email client, calculator, home file-manager, all of which were setup at installation with no input from me.

Quite amazing in my opinion!

There is, however, a way to configure extra mouse buttons if necessary.
```
# Entries to enable forward & backwards navigation in nautilus with mouse buttons.

#sudo apt-get install xvkbd xbindkeys x11-utils.

#Terminal command:-
#xev | grep ', button'         Press mouse buttons and note output, eg

#state 0x10, button 8, same_screen YES
#state 0x10, button 8, same_screen YES
#state 0x10, button 9, same_screen YES
#state 0x10, button 9, same_screen YES

#Back in terminal, we need to create a new file to configuration xbindkeys.

#gedit ~/.xbindkeysrc

#This will load up Gedit to add content to the new file. This file needs to contain the following:

#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
#  m:0x0 + b:8
#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
#  m:0x0 + b:9

#Notice the &#8220;b:8&#8243; and &#8220;b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse buttons are 6 and 7, then you need to change &#8220;b:8&#8243; and &#8220;b:9&#8243; to &#8220;b:6&#8243; and &#8220;b:7&#8243;, respectively.

#Set xbindkeys to autostart at session start in System->Preferences->Startup Applications.

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```
Note this was for Ubuntu so you will need to use kate (or whatever text editor you use) not gedit.  All this was needed in 10.04 but not in 12.04 nor in 14.04 which I am now using.

---

### Post by scottbomb on 2015-04-06
Interesting, thanks. Hopefully future versions of KDE will give more control over mouse buttons.

---

