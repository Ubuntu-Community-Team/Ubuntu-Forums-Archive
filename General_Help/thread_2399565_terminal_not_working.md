---
title: "terminal not working"
date: 2018-08-27
forum: General Help
---

### Post by pinto12 on 2018-08-27
So I see many threads regarding this weird issue but none that I checked helped. I have a VirtualBox Ubuntu 18.04.1 LTS and after last restart, clicking the terminal icon results in a few seconds "thinking" after which nothing happens.
Per other threads, I tried changing the locale file, taking a new .bashrc file, running sudo apt-get install gnome-terminal. All this via ALT-F2 window.
What else should I try? If new installations are required I only know how to do them with the ALT-F2 but it's a-bit quirky since it doesn't give feedback.

---

### Post by Holger_Gehrke on 2018-08-27
Have you tried starting the terminal by entering 'gnome-terminal' in the alt-f2 dialog? If that works than there's nothing wrong with the terminal-program itself or it's configuration; in this case the problem is probably with the .desktop-file used to start the gnome-terminal in '/usr/share/applications/' (or in '~/.local/share/applications/' if you created your own .desktop-file to start the terminal with some specific options).

If that doesn't work, you can try using 'xterm', an older terminal-program which should be installed by default. It's a very old program, therefore it's UI is ... unusual. You get the menus to change it's appearance (and some functionality) by holding the ctrl-key and pressing one of the three mouse buttons (this is important since it starts up with an eye-straining tiny font by default). I wouldn't want to use it permanently, but in an emergency it can be used to fix things ...

Holger

---

