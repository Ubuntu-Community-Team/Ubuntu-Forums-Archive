---
title: "How do I run an executable in a specific resolution?"
date: 2012-12-16
forum: General Help
---

### Post by khometmibro on 2012-12-16
Okay, so I'm trying to run the War For The Overworld showcase demo and theres no way to configure the resolution it plays in since it's incomplete. So it just opens in 1366x768. How do I make it run in 800x600 without setting my monitor to that resolution?

I remember in windows cmd prompt you could do something like  executable.exe -width 800 -height 600 or something like that. What parameters do I use in terminal?

Thanks guys.

---

### Post by mcduck on 2012-12-16
since the parameters are given to a program, not the terminal (or the shell), having such option depends if the program you are running has the option...

So you should check the game's documentation if it allows you to set the resolution, and how.

---

### Post by Impavidus on 2012-12-16
If you can't find an in-game option to set the screen resolution, you may be able to write a tiny shell script that changes resolution, starts the game and, after exiting the game, resets the resolution. The xrandr command can be used to change resolution.

---

### Post by khometmibro on 2012-12-16
Thanks guys.


The game itself is not complete (it's just a little showcase demo) so there is no options menu


EDIT: I can't use xrandr either since for some reason nvidia-current doesn't allow me to use anythign other than the native monitor resolution (1366x768). I have to switch to nouveau to run it. If only there were a way to play the game at 800x600 in windowed mode... but alas...

---

