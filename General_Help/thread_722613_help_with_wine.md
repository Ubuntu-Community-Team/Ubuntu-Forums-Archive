---
title: "help with wine"
date: 2008-03-12
forum: General Help
---

### Post by Papas228 on 2008-03-12
hi, i've been using ubuntu know for sometime and i'm still a noob to things. i'm currently running gutsy. i've been able to get compiz to work pretty well accept i guess compiz hates ati cards. now my question about wine is, i can get programs and games to install like steam, and guild wars. now steam works fine for me, but if i try to run guild wars it will start to load, then the screen goes blank for a second or two and then it changes my resolution and that's it i have to reboot. i was wondering if there was a work around this or what. thanks for any useful info. 

my specs are: tforce 550 SE, Amd 5600, and an ati hd3870. thanks again

---

### Post by doorknob60 on 2008-03-12
Try disabling Compiz. Sometimes Compiz can cause problems with full screen games, especially using Wine. Also, graphics performace is always better with Compiz turned off. To turn it off, just press alt-f2 and type this:
```
metacity --replace
```
To turn Compiz back on, press alt-f2 and type this:
```
compiz --replace
```

You could even write a script that turns off compiz before you play, and turns it back on when you're done (assuming it would help):
```
#!/bin/bash
metacity --replace &
WINEDEBUG=-all wine "C:\path to program"
compiz --replace &
```

---

