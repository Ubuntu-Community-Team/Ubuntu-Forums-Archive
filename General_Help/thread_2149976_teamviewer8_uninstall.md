---
title: "teamviewer8 uninstall?"
date: 2013-05-30
forum: General Help
---

### Post by candtalan on 2013-05-30
Teamviewer 8  installs via ubuntu software centre (after download of deb file) however, it does not uninstall via the software centre (version 7 was well behaved). I want to uninstall it and would be grateful for some advice on how to do this.

Downloaded from:
[http://download.teamviewer.com/download/teamviewer_linux.deb](http://download.teamviewer.com/download/teamviewer_linux.deb)

tia

---

### Post by plucky on 2013-05-31
> **candtalan said:**
> Teamviewer 8  installs via ubuntu software centre (after download of deb file) however, it does not uninstall via the software centre (version 7 was well behaved). I want to uninstall it and would be grateful for some advice on how to do this.

Downloaded from:
[http://download.teamviewer.com/download/teamviewer_linux.deb](http://download.teamviewer.com/download/teamviewer_linux.deb)

tia

From a terminal ```
sudo dpkg -r teamviewer8
```

Good Luck

---

### Post by candtalan on 2013-05-31
Thanks!
I had to use simply  'teamviewer'
```

candt@novatech1:~$ sudo dpkg -r teamviewer
(Reading database ... 570807 files and directories currently installed.)
Removing teamviewer ...
wine: /home/user1/.config/teamviewer8 is not owned by you

```
the wine  .config  stuff could be deleted  by me without privilidge escalation. 
Thanks again

---

### Post by Thunder7102 on 2013-05-31
I got the following to work just fine: 
```

sudo apt-get autoremove teamviewer

```

---

