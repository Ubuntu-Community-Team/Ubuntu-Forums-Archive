---
title: "Setting Up a Choice Between CLI or GUI in GRUB"
date: 2012-12-01
forum: General Help
---

### Post by morbid_bean on 2012-12-01
I am running Xubuntu 12.10 on an old Dell Optiplex 260.  Doing real well :D

I Use this box as a basic dedicated Minecraft server for me and my friends to play together.

I am wanting to conserve as much resources as possible, and I would think having GUI or X loaded up while running it would suck a little bit of performance out of it.

What I would Like to do is set an option on Grub to Boot to a GUI and a CLI session if possible.  How would this be accomplished?

I am also aware pressing Ctrl+Alt+F1 in gui will go into a Fullscreen CLI and Ctrl+Alt+F7 will go back out, but does being in that CLI still have GUI running in the background?

---

### Post by Cheesemill on 2012-12-01
You can achieve this using the grub menu but there is an easier way.

The following command will disable the display manager meaning your system will always boot in CLI mode:
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```

If you want to start the GUI just login and type:
```
startx
```

---

### Post by morbid_bean on 2012-12-01
> **Cheesemill said:**
> You can achieve this using the grub menu but there is an easier way.

The following command will disable the display manager meaning your system will always boot in CLI mode:
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```

If you want to start the GUI just login and type:
```
startx
```

AWESOME!  Not quite what I was looking for, but this works even better!

---

### Post by Cheesemill on 2012-12-01
> **morbid_bean said:**
> AWESOME!  Not quite what I was looking for, but this works even better!
Glad it works :)

As I said earlier it is possible to use the method you were thinking of, it just involves a bit more work:
[http://ubuntuforums.org/showthread.php?t=1947925](http://ubuntuforums.org/showthread.php?t=1947925)

---

