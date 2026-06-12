---
title: "Made a big mistake with chown"
date: 2013-09-09
forum: General Help
---

### Post by ineuw on 2013-09-09
Mistakenly executed ```
sudo chown -R ineuw:ineuw /
``` forgetting to add the application name for deletion, and changed ownership to a LOT of OS files which shouldn't be changed, before I realized and hit Ctrl-Break. Is there a way to reverse my error?

---

### Post by lah7 on 2013-09-09
From my experience, it's pretty hard to completely reverse such changes, just like if you was to accidentally execute a dangerous command on **/** instead of **./**

Most important OS files are owned by **root**, so I would suggest changing them back as **root** being the owner.

However, I can't 100% certain about this. It's [COLOR=#b22222]really risky[/COLOR] and might misbehave the system due to permissions issues, since not all the files are owned by root, for example, a web server like Apache2 would need **www-data** as its owner.

---

### Post by ajgreeny on 2013-09-09
You may like to try ```
sudo chown -R root:root /
sudo chown -R ineuw:ineuw /home/ineuw
```This will firstly return the root file system, including your home,  to root ownership and then return your home to your own ownership though I admit I am not totally sure about its likely success, and may cause problems with ownership of some files in root which have other owners.

---

### Post by scbingham on 2013-09-09
Unfortunately your chances of correcting your mistake are incredibly slim. Any changes/updates you make in the future may have issues & you'll never know if it's a config or ownership problem.

Your best bet is a clean install. Save your /home & any other important data first.

---

### Post by ineuw on 2013-09-09
Sadly only a clean install will help as I can't even log in anymore. The data is secure. Thanks for all the replies.

---

