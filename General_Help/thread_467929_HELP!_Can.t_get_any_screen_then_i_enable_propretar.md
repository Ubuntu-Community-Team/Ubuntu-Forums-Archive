---
title: "HELP! Can.t get any screen then i enable propretary drivers."
date: 2007-06-08
forum: General Help
---

### Post by Azyx on 2007-06-08
How can i disable "propretary drivers" from terminal?

I Have an ATI-gfx-card and it dont work when i enable propretary drivers. My screen shut down when Ubuntu should load xorg, i think. the computer is on and i can go in throu the net (ssh).

Please help me get rid of the propretary-drives and have it as before.

---

### Post by Crafty Kisses on 2007-06-08
You can try to reconfigure your X server file, try the following:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Azyx on 2007-06-08
ok. Thanx, but i just erased the xorg.conf and copy a xorg.config.backup file to xorg.config. It worked :)  It's a little bad thing, that things you do easy, mark restriicted drivers, may get you computer to not start or disable the screen. How do you get "error safe" or terminal start in ubuntu feisty fawn? Do I need to edit in GRUB or is there any other place a can those how ubuntu should boot?

---

### Post by tyler_roach on 2007-06-08
If xorg can't start for some reason, your machine automatically fall back into command-line mode. This, more that likely will enable you to fix the problem.

---

### Post by Azyx on 2007-06-08
[That did not happend. I have to go in with ssh from another machine. I don't know what happend, but my gfx-card didn't send any signal to my monitor. It was totaly black and my monitor said: -No signal.

/azyx

QUOTE=tyler_roach;2806022]If xorg can't start for some reason, your machine automatically fall back into command-line mode. This, more that likely will enable you to fix the problem.[/QUOTE]

---

### Post by Crafty Kisses on 2007-06-09
> **Azyx said:**
> [That did not happend. I have to go in with ssh from another machine. I don't know what happend, but my gfx-card didn't send any signal to my monitor. It was totaly black and my monitor said: -No signal.

/azyx

QUOTE=tyler_roach;2806022]If xorg can't start for some reason, your machine automatically fall back into command-line mode. This, more that likely will enable you to fix the problem.

You do know the command to recover a backed up X server file?

---

### Post by Azyx on 2007-06-09
No. I dont know that command. I remove rm the xorg.conf and copy cp one of the different backupfiles I hade to the name xorg.conf.  And it worked :) . But if I did't have ssh I couldn't commin in to a terminal. I don't know how I stop feisty fawn to boot to normal. I have autologin activated.

> **Codename said:**
> You do know the command to recover a backed up X server file?

---

