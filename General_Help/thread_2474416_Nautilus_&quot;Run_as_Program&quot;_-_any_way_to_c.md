---
title: "Nautilus &quot;Run as Program&quot; - any way to change the terminal?"
date: 2022-04-28
forum: General Help
---

### Post by ariel on 2022-04-28
Just upgraded from 20.04 to 22.04, great upgrade overall however Files / Nautilus lost its ability to launch executable files by double clicking which I was used to.

I noticed 22.04 added a "Run as program"  context menu entry that helps a lot, however it opens gnome-terminal instead of my preferred terminal (tilix).
Further, I'd like to customize some command line options for the terminal, and use something like:

```
tilix --action session-add-down --focus-window -e $1
```

Is there a way to do this? I don't mind tinkering with system files if needed. I tried changing GNOME's default terminal to tilix to see if that helped but no luck. Any guidance/hint would be great

---

### Post by DuckHook on 2022-04-28
Please use only standard fonts and styles when posting. Your original post was unreadable on my browser.

---

### Post by Holger_Gehrke on 2022-04-29
Since I'm using XUbuntu with XFCE instead of Ubuntu with Gnome this is just a wild guess but it might work, depending on whether the context menu item explicitly calls 'gnome-terminal' or uses the generic 'x-terminal-emulator' set up through debian-alternatives. If it's the latter you can change what program gets called as x-terminal-emulator by running
```

sudo update-alternatives --config x-terminal-emulator

```
You will be presented with a menu. Select the program to use as x-terminal-emulator by entering the number for it. Alternatively you could run 'sudo update-alternatives --set x-terminal-emulator /usr/bin/tilix.wrapper' (might just be '/usr/bin/tilix', I'm going by the list of files on packages.ubuntu.com ...).

Holger

---

### Post by ariel on 2022-06-17
@Holger thanks! I did that, selected 'tilix.wrapper' as my default terminal, the behavior I am seeing is weird, when I select "run as program" on a script, I see gnome-terminal and it's purple background flashing, and then the script opens in tilix. It's very strange.

---

