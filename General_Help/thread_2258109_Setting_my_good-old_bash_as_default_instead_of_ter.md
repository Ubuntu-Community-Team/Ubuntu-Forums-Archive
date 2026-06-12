---
title: "Setting my good-old bash as default instead of terminator"
date: 2014-12-24
forum: General Help
---

### Post by goghvv on 2014-12-24
Hi.
I'm using [Geany IDE]("http://www.geany.org/") to write python code for a couple of months now.
When you run your code with geany, it automatically opens a new terminal window to show the program output.
Lately I installed Terminator, and ever since, whenever I run code from Geany, it opens the Terminator instead of the good-old Ubuntu's bash.
I guess this is beacuse the terminator is now my default shell instead of the old one, but I don't want it to be the default shell. I want the old one back, and to still keep terminator installed on my machine (sometimes it is useful for me).

How can I set my previous bash as the default one again?

---

### Post by Holger_Gehrke on 2014-12-24
Actually, 'Terminator' is not a shell but a terminal emulator, the shell that runs in it is probably still the bash. Look in Preferences->Tools->Terminal. Should this option be set to 'x-terminal-emulator' plus some options then it's using the default as set through the Debian alternatives system. Use the command 'update-alternatives --config x-terminal-emulator' to chose your favourite. The default terminal emulator in Ubuntu is gnome-terminal.

---

