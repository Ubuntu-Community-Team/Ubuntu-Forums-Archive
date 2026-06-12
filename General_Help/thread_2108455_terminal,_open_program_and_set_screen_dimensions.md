---
title: "terminal, open program and set screen dimensions"
date: 2013-01-24
forum: General Help
---

### Post by alphaamanitin on 2013-01-24
I want to open a program, specifically ADOM [www.adom.de](www.adom.de), and set the scree to a resolution that it will play under.  

I currently have to maximize the terminal screen, then run adom.  Is there anything I can do that makes it where the screen automatically adjusts to the screen size needed when I run the program?  I assume I would then add this to the ~/.bashrc alias lists and make a new alias for the command.

Thanks,

AlphaA

---

### Post by Toz on 2013-01-24
Add the following command to ~/.bashrc:
```
alias adom='xfce4-terminal --geometry 77x25 -x /path/to/adom'
```
...make sure you change "/path/to/adom" to be the real path to your adom executable.

To have it take effect for your current terminal session, source the newly updated .bashrc file:
```
. ~/.bashrc
```

Then in the same terminal window, run:
```
adom
```

---

### Post by alphaamanitin on 2013-01-24
Great! Thanks, works perfectly.

Id

---

### Post by neu2buntu on 2013-01-24
another method is to use gdevilspie, you can set rules for size, position on screen, start minimized etc. once your rules are set you can just run a bash script to run the backend devilspie, so there will not be an extra window open i.e gdevilspie.    

oh and the script can be run from your startup programs ( the gear at the top right of the screen > startup applications )

---

