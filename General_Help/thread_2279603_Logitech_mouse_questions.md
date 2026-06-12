---
title: "Logitech mouse questions"
date: 2015-05-24
forum: General Help
---

### Post by netopalis45 on 2015-05-24
I use a Logitech M560 mouse with unifying receiver and have been trying to configure the extra buttons on the side and top. For some reason the lower thumb button is mapped to the letter "d" and I can't get the other one to do anything. I have tried using xbindkeys to remap these buttons but that hasn't helped. Xbindkeys uses .xbindkeysrc as a configuration file. Are there any other ways to configure the mouse buttons that I could use or that may be mapping the button to the letter "d"?

Thanks in advance

---

### Post by bwanaaa on 2016-02-13
I found that xte is flakey.
My sequence for mapping the the thumb button of my logitech 518 to 'control W' to close tabs and windows never worked well with xte not sequencing properly.
For example this failed:
```
"xte 'keydown Control_L' 'w' 'keyup Control_L'"
 b:8
```

as did this:
```
"xte 'keydown Control_L' 'w' 'keyup Control_L'"
 b:8 + release
```

I also noticed that xte was SLOOOW.
I tried xvkbd and it works well.

OF course you have to get xvkbd with this:
```
sudo apt-get install xvkbd
```

Put this in your .xbindkeysrc file in your home directory
```

"xvkbd  -text '\C\[w]'"
m:0x0 + b:8
```


and restart xbindkeys
pkill -f xbindkeys  && xbindkeys

---

