---
title: "bash script - Opening terminal in workspace 2"
date: 2015-09-24
forum: General Help
---

### Post by Tony T on 2015-09-24
Greetings from Michigan!

When I run my bash scripts it opens the program (gnome-terminal command line) in my current workspace, then I move them. How can I have the bash script open the terminal in workspace 2 ??

---

### Post by CantankRus on 2015-09-24
Hi,
You can install and use ccsm(compizconfig-settings-manager) to set gnome-terminal to open in workspace 2.
```
sudo apt-get install compizconfig-settings-manager
```

After installation, search "ccsm" and launch from dash.
Then use ccsm > window management > place windows > fixed window placement
[ATTACH=CONFIG]264640[/ATTACH]

If you only want terminals opened through scripts to open in workspace 2 you may need
to set up and use terminal profiles and set ccsm only to move terminal windows of a particular title.
[ATTACH=CONFIG]264641[/ATTACH]  [ATTACH=CONFIG]264642[/ATTACH]

---

### Post by Tony T on 2015-09-25
Thank you CantankRus! Just what I needed.

---

