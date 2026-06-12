---
title: "nvidia-settings keyboard layout resetting"
date: 2007-09-05
forum: General Help
---

### Post by phillips321 on 2007-09-05
Hi guys,

every time i VNC from work to home i turn off my right hand screen using nvidia-settings.

Then when i get home again i use nvidia-settings to renable it again.

The problem is that it saves the xorg.conf without any keyboard option so it default to us, sadly im from the uk so each time i have to manually add the line.

```
Option "XkvbLayout" "gb"
```

Not a huge problem but kinda of a pain in the ****.

Anyone got any ideas so i can fix this?

cheers

---

### Post by Nythain on 2007-09-05
so you have two different setups you use??? is that right... if so why not just create two different /etc/X11/xorg.conf files maybe one called xorg.conf.right and xorg.conf.noright then just sudo cp /etc/X11/xorg.conf.whichever /etc/X11/xorg.conf and control alt backspace to reload X... or cp the file before loading X...

The problem is, nvidia-settings is ALWAYS going to set up a default xorg.conf when you tell it to... and i dont think (dont quote me on this, i could be wrong) there's a way to have it add arguments/options/variables or not use certain ones when it does it. I guess you could google the nvidia-settings program itself, maybe google man nvidia-settings and see if there are any speciall arguments you can run it with that will have it add that line when it creates the new xorg.conf

and thats all assuming i understood your problem right

---

