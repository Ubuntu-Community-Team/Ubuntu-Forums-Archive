---
title: "Ubuntu 22.04.3 on X1 Extreme won't turn off"
date: 2023-10-05
forum: General Help
---

### Post by Feddy on 2023-10-05
I was trying to solve some problem with sound and BT on my X1E. After  reinstalling the drivers, I seem to get them back to work, but now the  system doesn't turn off after I click the Power Off option. It does  close the apps and something else, and then freezes at the interface  with [red Lenovo and Ubuntu logos on black background]("https://i.stack.imgur.com/4uMYE.jpg").  The only way I can turn if off completely is to press the Reset button  on the bottom of the laptop which disconnects the internal battery. How  can I diagnose/fix it?


     
[IMG]https://i.stack.imgur.com/4uMYE.jpg[/IMG]

---

### Post by newcfd on 2023-10-06
take a look at syslog first

---

### Post by MAFoElffen on 2023-10-07
The syslog stops writing at a certain point. If I am trying to debug a shutdown problem, I use journalctl, usually with something similar to:
```

journalctl -b 2 -g 'systemd' --no-pager | grep -A 200 -Ei 'shutdow'

```

---

