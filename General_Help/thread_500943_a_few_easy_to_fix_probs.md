---
title: "a few easy to fix probs"
date: 2007-07-14
forum: General Help
---

### Post by skaspud on 2007-07-14
right now i have a mil things wrong with ubuntu
big ones:
1. i can't get beryl to work
2. i can't get wine to work
3. i can't get windows on my other harddrive to boot

1. i have beryl fully installed using [http://wiki.beryl-project.org/wiki/I...eisty_with_ATI](http://wiki.beryl-project.org/wiki/I...eisty_with_ATI)
i have the driver for my ati x850 pro working fine and everything
the lil beryl icon just sits up top and chills there not doing anything, i've rightclicked-window manager and tried switching to beryl from gnome and it would reload the windows and everything but nothing happened...

2. i've got wine all downloaded and installed, i have it installed but i can't get it to start up,it's not in the applications menu.

3 this is a big one...
i installed ubuntu 6.06 on a second hard drive in my computer, using this i was easily able to switch from ubuntu and back to windows by just switching the bios when booting up. but after i installed 7.04 i tried booting the windows bootup from the bootup menu that ubuntu shows, it starts the windows splash screen but then it doesn't work, it tries loading up GRUB. then says error17 (i think). I can access my C: partition from ubuntu when its hooked up, but i need the stuff from my other partitions. especially the programs and such.

Thanks (hopefully) in advance :]

edit:
i installed my graphics driver using envy- in case it helps...

---

### Post by AlexThomson_NZ on 2007-07-15
A couple of things-

1 Use compiz-fusion instead of Beryl (Beryl has merged with Compiz into this).  You should probably try running Beryl from the command-line and seeing what the problem is though.

2) I'm not sure Wine has a graphical front-end.  I run it from the command-line:
wine /path/to/windows/program/name &

---

