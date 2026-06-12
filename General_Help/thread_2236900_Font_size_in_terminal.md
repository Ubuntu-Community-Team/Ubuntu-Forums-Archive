---
title: "Font size in terminal"
date: 2014-07-29
forum: General Help
---

### Post by chuck598 on 2014-07-29
How do I change the display font size in terminal as it is way to small for me without a magnifying glass?

---

### Post by sudodus on 2014-07-29
What terminal do you mean?

- a text screen or

- a terminal window?

If you mean a terminal window, there is often a pull-down menu, where you select preferences, profile settings or something similar.

---

### Post by egeezer on 2014-07-29
On the menu at the top of the terminal window click on Edit > Preferences.  Then you can go wild (font, color, etc)

---

### Post by ajgreeny on 2014-07-29
Exactly how depends on the DE you are using (xfce, gnome, unity, kde, lxde) and the terminal application that is using, but it will be somewhere in the Edit ->Preferences or Profile menu.

You can also edit the hidden **.bashrc file** in your home to get a coloured prompt, and edit root's **.bashrc** file to get a different colour prompt for a root terminal if you use such things.  I do use a root terminal sometimes so have set my user terminal with a [COLOR=#008000]green[/COLOR] prompt, and the root terminal with a [COLOR=#ff0000]red[/COLOR] prompt.  I find it a good reminder to be much more careful.  Come back here for details if that sounds useful or of interest to you.

---

### Post by chuck598 on 2014-08-04
Hi:
How do I change the display font size in the terminal window as it is way to small for me without a magnifying glass?
Using Ubuntu 14.04
Don't see a menu to make changes with.
I am a user & not great @ finding things.
Chuck

---

### Post by OriTheEep on 2014-08-04
If you are using Unity, the menus have migrated to the top left of the screen and only appear when the mouse cursor passes over them. Time to go hunting but click in the Terminal window first to make sure you get the right menu!

---

### Post by sudodus on 2014-08-04
Many programs respond to the hot-key combination

[SIZE=4]***ctrl +***[/SIZE] (press the ctrl key and then the plus key)
Each time the font size increases, so you can increase it step-wise.

[SIZE=4]***ctrl -***[/SIZE] (press the ctrl key and then the minus key) will decrease the font size

[SIZE=4]***ctrl 0***[/SIZE] (press the ctrl key and then the zero key) will reset the font size to the default size

This way you can make more or less temporary changes.

-o-

Persistent changes are made as described in previous posts (via settings or preferences menus).

---

### Post by chuck598 on 2014-08-05
Re: Font size in terminal
Hi:
How do I change the display font size in the terminal window as it is way to small for me without a magnifying glass?
Using Ubuntu 14.04
Don't see a menu to make changes with.
I am a user & not great @ finding things.
Chuck
---***---
OK, the menu @ teh top allows you to: minimize maximize, move, resize & always on top plus close.

The control plus etc works on the web windows but not for me in the terminal mode.

Any other ideas?
Chuck

---

### Post by vasa1 on 2014-08-05
With the terminal window on top, in focus, active, press **Alt+E** together. You should get a drop-down. Look for something like **Preferences** and take it from there.

---

### Post by sudodus on 2014-08-05
> **chuck598 said:**
> ...

The control plus etc works on the web windows but not for me in the terminal mode.

Any other ideas?
Chuck

The control plus etc work for me in terminal windows as well as in browser windows, but not in text screen mode, if that is what you mean by 'terminal mode'.

Text screen mode:

Depending on your system and hardware, it might be possible to change the text size in the grub settings. See these links

[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)
[URL="http://www.linuxquestions.org/questions/ubuntu-63/changing-virtual-console-screen-resolution-860061/"]
http://www.linuxquestions.org/questions/ubuntu-63/changing-virtual-console-screen-resolution-860061/[/URL]
[URL="https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2"]
https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2[/URL]

---

