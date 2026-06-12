---
title: "Delay conky startup"
date: 2006-07-18
forum: General Help
---

### Post by Topper_H on 2006-07-18
Hi all,

I use conky as my favourite hardware monitor. I added it in my session startup list but here's my problem :
It seems that conky starts too early : Its window (which is supposed to be below all others) is quickly covered by my wallpaper when my session launches. I have to kill and restart it to have it show above my wallpaper.

I tried to tweak conky's order in the session manager (it is set to 50 by default) but this number goes back to default (50) everytime I restart my session.

Help anybody ?

---

### Post by trent dillman on 2006-07-20
Try turning conky on with a shell script that sleeps:
```
#!/bin/bash
sleep 30
conky
```

NOTE: I haven't tried this, as I have my desktop icons turned off completely to accomodate my desktop terminal (gotta love devilspie !!)

---

### Post by Ramses de Norre on 2006-07-20
Or just set the command to ```
sleep 10 && conky
```

---

