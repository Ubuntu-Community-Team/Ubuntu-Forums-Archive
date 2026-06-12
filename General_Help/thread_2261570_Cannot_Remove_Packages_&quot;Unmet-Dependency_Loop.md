---
title: "Cannot Remove Packages: &quot;Unmet-Dependency Loop&quot;"
date: 2015-01-19
forum: General Help
---

### Post by thatstheway on 2015-01-19
I'm running 12.04.5 and I have [COLOR=#000000][FONT=Arial]linux-image-3.13.0-44-generic teed up in Update Manager to be installed, but I can't install this, because it requires a PAE-enabled [/FONT][/COLOR]cpu and I haven't got one, yet. Meaning, I want to do [this fix]("http://ubuntuforums.org/showthread.php?t=2113826&page=2&p=12504589#post12504589"), but I can't install anything, because of two packages that depend on [COLOR=#000000][FONT=Arial]linux-image-3.13.0-44-generic: 
[LIST]
[*][COLOR=#000000][FONT=Arial]linux-image-generic-lts-trusty
[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]linux-generic-lts-trusty[/FONT][/COLOR][/FONT][/COLOR] 
[/LIST]
[COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]
Everything I do in the Software Center or the terminal, results in an error around the unmet dependencies of these two packages, and since I can't install the thing they need, I need to delete these packages, try the fix above, and then try to install everything. 

I've tried 
[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]sudo apt-get -f remove linux-image-generic-lts-trusty[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo apt-get -f remove linux-generic-lts-trusty[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get --purge -f remove linux-image-generic-lts-trusty[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get --purge -f remove linux-generic-lts-trusty[/FONT][/COLOR]


```[COLOR=#000000][FONT=Arial]

with and without the -f, and nothing has worked. Neither has autoremove, autoclean, or clean. 

Any advice would be most appreciated! 


[/FONT][/COLOR]

---

### Post by thatstheway on 2015-01-19
Ah this worked:
```
[COLOR=#000000][FONT=Arial]sudo dpkg --remove --force-remove-reinstreq linux-image-generic-lts-trusty[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo dpkg --remove --force-remove-reinstreq linux-generic-lts-trusty[/FONT][/COLOR]
```

---

### Post by fantab on 2015-01-19
Post the output of:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

edit: Nevermind! just read that you've fixed the issue.

---

### Post by thatstheway on 2015-01-19
Np, fantab! This stuff gets so crazy sometimes, the more solutions/things to try we have up here, the better!

---

