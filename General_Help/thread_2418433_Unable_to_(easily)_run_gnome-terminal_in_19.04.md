---
title: "Unable to (easily) run gnome-terminal in 19.04"
date: 2019-05-06
forum: General Help
---

### Post by defaria on 2019-05-06
Updated my laptop to Ubuntu 19.04. Now I can no longer find and run gnome-terminal, 'cept I discovered if I right click on the desktop and select Open in Terminal. IOW if I click on Activities in the top left or hit the command key and type "terminal" I do not see gnome-terminal as an option. If I run Synaptic I can verify that gnome-terminal is indeed installed. If I right click on the desktop and select Open in Terminal a gnome-terminal does indeed start so I know it's there. Why isn't it found when I type in "terminal"? Also, I'd like to "pin" the terminal to dock but I don't see how.

I'm running gnome-shell version 3.32.0. I prefer gnome version 2.x and compiz but I can't seem to get that working. I also like a number of icon launchers I used to configure in the old gnome-panel.

What terminal do you run? How do you run it? How can I pin gnome-terminal to the dock? Finally, how can I configure icon launchers.

---

### Post by dragonfly41 on 2019-05-06
> [COLOR=#000000]Why isn't it found when I type in "terminal"[/COLOR][COLOR=#000000]

Try typing gnome-terminal instead of terminal. Or keys ctrl+alt+t.
In Ubuntu 16.04 I use docky for docking apps. I don't know if it is in 19.04.
You might try installing yakuake as another terminal option. Toggle using F12.[/COLOR]

---

### Post by #&amp;thj^% on 2019-05-06
Docky is not in 19.04 just to help.
```
$ apt search docky
Sorting... Done
Full Text Search... Done

```
And I'm not sure if there is a PPA for the version needed.
Plank is though.
```
apt search plank
plank/disco,now 0.11.4-4 amd64 [installed]
  Elegant, simple, clean dock

```

---

### Post by Holger_Gehrke on 2019-05-06
Have you tried the hotkeys for the terminal ? For as long as I can remember, the terminal was always assigned to ctrl-alt-t and/or super-t ("super" is an additional modifier key, normally assigned to the key with the Windows-Logo).

Holger

---

### Post by corradoventu on 2019-05-08
Open the terminal by right click on the desktop, the terminal appears on the dock, right click on the terminal icon an select 'add to favorites' so you will have the terminal in the dock

---

