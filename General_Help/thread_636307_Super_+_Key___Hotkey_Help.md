---
title: "Super + Key   Hotkey Help"
date: 2007-12-09
forum: General Help
---

### Post by dethredic on 2007-12-09
Is there any way to make Super+D show the desktop and just super do the expo effect. (I have compiz installed). It is ok for it to be super + a key is necessary.

---

### Post by avik on 2007-12-09
You have CompizConfig Settings Manager installed, right?  You can look in Add/Remove Programs for ccsm.  You can then open it from System->Preferences->Advanced Desktop Effects Settings.

Go to General Options->Actions->General.  Change "Hide all windows and focus desktop" to have a keyboard shortcut of Super+D.

For the expo effect, you can't use *just* the Super key as it's used as a modifier, not a single key.  Go down to Expo->Actions->Bindings.  Change Expo to have a keyboard shortcut of whatever.  I use Super+E (and I have it set to the bottom right of the screen).

Hope that helps.

---

### Post by dethredic on 2007-12-09
Great, the desktop one works great, but I guess I had the wrong plugin, cause expo is not what I thought it was. What is the effect that shows all your windows smaller and not overlapped?

Edit2: This is the effect I want a Super+E hotkey for:


[IMG]http://img70.imageshack.us/img70/5168/thiseffectni7.png[/IMG]

EDIT: After I made that change, some of my other effects didn't work, such as the windows going transparent when I drag them. I restarted my computer to fix this, but then my screen resolution was stuck at something weird (1600x1200) although I don't have a wide screen. What was weider was that it wasn't actually 1600x1200 because it worked fine on my square monitor. I restarted again, and this time i got the true 1600x1200 because i could see the left or right of my screen. I changed the resolution back to 1280x1024 and now everything is working fine. 
Why would I have had to go through all of that?

---

### Post by dethredic on 2007-12-09
Ohh, Can I make a Super+L hotkey for screen lock??

---

### Post by dethredic on 2007-12-09
anyone?

---

### Post by UK-Wobbie on 2007-12-09
> **dethredic said:**
> Ohh, Can I make a Super+L hotkey for screen lock??

What button is the Super? :confused:

---

### Post by dethredic on 2007-12-09
The windows Key

---

### Post by dethredic on 2007-12-10
anyone?

---

### Post by vapore0n on 2007-12-10
in the Compiz settings, in the Command area, set command 0 (or any number) to
gnome-screensaver-command -l
then set in the Actions area whatever key you want (Super-L)

---

### Post by dethredic on 2007-12-10
I do not see a command area.

---

### Post by dethredic on 2007-12-10
Ok, the effect I was talking about before was the viewport windows found under the Desktop tab in the Gnome Compiz preferences.

I set it to Super+e and it works, but with flaws. I have to hold down the windows key after pressing this combo for it to stay in the "viewport windows", otherwise it just reverts back to normal view.

Also, I still don't understand how to do the lock screen one.

---

### Post by dethredic on 2007-12-11
Ok i got the super+e working, now i just need the screen lock.

---

### Post by theit8514 on 2007-12-12
In my CompizConfig 0.5.2, go to the main screen, General Options at the top, Commands tab

Set command line 0 to 'gnome-screensaver-command -l' w/o the quotes

Then go to actions tab and change Commands > Run command 0 to Super+L.

-J

---

