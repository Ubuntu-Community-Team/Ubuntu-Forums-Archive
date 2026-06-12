---
title: "Conky on netbook probs"
date: 2013-04-24
forum: General Help
---

### Post by musicmanbiker on 2013-04-24
Hi all, haven't seen this before. My conky on the desktop is great, lifted the code from the long conky thingie. Did the same for my HP 1100 netbook and it will run but in the terminal. Can't get it to come up on the screen. Any ideas for a linux newbie? John

---

### Post by Frogs Hair on 2013-04-24
Check the x-y coordinates , it may be not be able to display due to position if there is a difference in monitor size. The type of conky window can sometimes be a factor also.

Look For: own-window-type  
```
 man conky
```
Example- position may vary
```
gap_y 80
gap_x 30
```

---

### Post by musicmanbiker on 2013-04-24
Thanks for trying Frogshair. I changed some of the parameters but no change. Will work on it some more later. Being "elderly" I don't know much about this but we need to continue to learn or may as well give up. John

---

### Post by nerdtron on 2013-04-24
I have some problems in conky before when used in LXDE. I managed to show conky by issuing ```
killall pcmanfm
``` which will make my desktop icons disapper. Then changing these parameters on the conky configuration.
```
[FONT=monospace]own_window yes[/FONT]
[FONT=monospace]own_window_type desktop # Try also 'normal' or 'override'[/FONT]
```

---

