---
title: "Can't run updates"
date: 2013-06-12
forum: General Help
---

### Post by brickmack on 2013-06-12
[COLOR=#000000][FONT=Verdana]When I try to run updates in ubuntu, I run 'apt-get update', which runs fine, but when I do 'apt-get upgrade' or 'apt-get autoremove' it returns:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Unable to lock directory /var/cache/apt/archives/[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I think this might be a result of a failed installation of a package a few days ago (It sometimes tells me something about needing to run 'dpkg --configure -a', which only sometimes works) when it froze during installation and I just cancelled it. Any help?

I'm running Ubuntu 13.04[/FONT][/COLOR]

---

### Post by QIII on 2013-06-12
Hello!

That often happens when you have a GUI package manager open and try to do updates via the terminal, but that is not the only reason it might.

Is that what is going on?  If so, use one method or the other, but don't have both going on at the same time.

Best wishes!

---

### Post by brickmack on 2013-06-12
No, I actually dont even have a GUI on this machine. Ended updeleting [COLOR=#000000][FONT=Verdana]/var/cache/apt/archives/lock[/FONT][/COLOR]&#8203; and that fixed it[COLOR=#000000][FONT=Verdana][/FONT][/COLOR]

---

### Post by ShadowVegan on 2013-06-12
Make sure you type 'sudo' at the beginning of the commands so as to run them as a super user. Limited users don't have full access to updates, upgrades, installations, etc.
```
sudo apt-get update && sudo apt-get upgrade
```

---

