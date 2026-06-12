---
title: "Latte dock, Launcher producing error, UM 22.04"
date: 2024-11-08
forum: General Help
---

### Post by SciGuy1872 on 2024-11-08
Hi.  When clicking on the launcher in the Latte dock that is started by the  following terminal command: python3 -m katrain, I get an error message (see picture). The usual game runs when this command is pasted in  terminal.  How do I get the Latte launcher to enter this command in terminal, instead of the konsole the error refers to?  I figure this  problem will be easy to solve, so I just made sure the command is correct in the mozo.desktop file. I actually posted this thread on the Ubuntu Mate's community, but after applying the suggestion to edit the file referenced, discovered it already contained the line Terminal=true.  Thanks.

---

### Post by SciGuy1872 on 2024-11-08
Here is the code of the file referenced in the error message (mozo-made-1.desktop)

```

1#!/usr/bin/env xdg-open
 
2

3 [Desktop Entry]

4 Version=1.0

5 Type=Application
 
6 Terminal=true

7 Icon=/home/anthony/.katrain_master/screenshots/analysis.png

8 Name=Katrain

9 Exec=python3 -m katrain

10 Comment=Train with Katago engine
```

---

### Post by SciGuy1872 on 2024-11-08
I solved the issue by installing konsole--emulator for terminal started Katrain when Latte launcher clicked.

---

