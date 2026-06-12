---
title: "Map mouse button to Window Spread"
date: 2015-12-04
forum: General Help
---

### Post by DigiAngel on 2015-12-04
So I have an Evoluent mouse with a lot of buttons.  I'm switching machines, and for the life of me I don't remember hoe I did this.  I still have the old machine and can find any config files, but I'm having a hard time figuring out how I managed this.  It's not done using compiz manager as I've looked.  I have xdotool that I can tell, although I do have it installed.  I do have xbindkeys installed, but that's just for mapping a key combo to pm-suspend.  Thanks for any assistance....I feel like an idiot for not remembering how

---

### Post by DigiAngel on 2015-12-05
Well I had to use a different method using xfe (xautomation package) and xbindkeys as shown below:

```
# Open Window Spread
"xte 'keydown Super_L' 'key w' 'keyup Super_L'"
b:9 + release

```

along with having /usr/bin/xbindkeys_autostart autostart.

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

