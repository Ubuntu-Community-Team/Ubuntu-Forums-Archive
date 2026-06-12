---
title: "apply button not reachable in wine"
date: 2008-03-01
forum: General Help
---

### Post by SuperGO on 2008-03-01
i have been trying to install programs using wine but i can never get past the simple step of applying wine. when i open wine  i cannot move or resize the screen to get to the apply button to apply the settings. what can i do to solve this problem?

---

### Post by gobbles414 on 2008-03-01
SuperGO,

If you installed the Ubuntu version of Wine instead of the version from the Wine website, you should be able to configure Wine by going *Applications => Wine => Configure Wine*. If you don't have that menu, type **winecfg** into *Applications => Accessories => Terminal*. Try changing the graphics settings in Wine. And although the Windows 2000 setting is fine for most Windows programs, you may need to switch it to Windows 95 or 98 for older programs. Likewise, you may need to use the XP or Vista settings for newer software.

As always, **check Wine's [AppDB]("http://appdb.winehq.org/")** to learn if your Windows programs are compatible with Wine.

---

### Post by spupy on 2008-03-01
> **SuperGO said:**
> i have been trying to install programs using wine but i can never get past the simple step of applying wine. when i open wine  i cannot move or resize the screen to get to the apply button to apply the settings. what can i do to solve this problem?

Have you tried holding Alt and dragging the window?

---

### Post by SuperGO on 2008-03-02
i tried using alt click but is only moved the setup screen around inside the wine screen. i tried to change the size of the wine screen by typing in new dimensions but since i couldnt reach the apply button, the changes did not take affect. all i want to do is press the button but its off the screen.

---

### Post by Oldsoldier2003 on 2008-03-02
> **SuperGO said:**
> i tried using alt click but is only moved the setup screen around inside the wine screen. i tried to change the size of the wine screen by typing in new dimensions but since i couldnt reach the apply button, the changes did not take affect. all i want to do is press the button but its off the screen.

If you know the tab order of the button, you could try tabbing "x" times then hitting return.... kinda like doing a blind shutdown on a windes box :)

---

### Post by spupy on 2008-03-02
I think Ctrl+Enter is a Windows combo for OK, maybe works for apply too?

---

### Post by SuperGO on 2008-03-07
Thank you soooooo much! wine took the changes into effect with **[B]ctrl + ENTER**[/B] now to install wow. anyone?

---

### Post by Gondee on 2008-07-08
It happends if you put wine 1.0 in a 800x 600 box.

The apply button to fix it becomes unreachable

This helped me fix it Thanks

---

