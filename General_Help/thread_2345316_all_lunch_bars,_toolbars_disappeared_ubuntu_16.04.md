---
title: "all lunch bars, toolbars disappeared ubuntu 16.04"
date: 2016-12-02
forum: General Help
---

### Post by abouzeid007 on 2016-12-02
Hi all, 

Unfortunately, i am a beginner with ubuntu and started to like it but i had this problem made me crazy. 

All lunch bar and tool bars had disappeared, I had searched for some solutions but nothing work. 

I tried with sudo apt-get update but gave me errors. 

Also i had this when i am log into the ubuntu, the system is running in low-graphics mode.

[ATTACH=CONFIG]272519[/ATTACH][ATTACH=CONFIG]272520[/ATTACH][ATTACH=CONFIG]272521[/ATTACH]

---

### Post by #&amp;thj^% on 2016-12-02
Try this:
```
sudo apt install unity-tweak-tool
unity-tweak-tool --reset-unity
dconf reset -f /org/compiz/
setsid unity
```
Post any errors using code tags,,,easier to read.

---

### Post by abouzeid007 on 2016-12-03
I got error message for the first code saying that, " unable to fetch some archives.... "

---

### Post by #&amp;thj^% on 2016-12-03
> **abouzeid007 said:**
> I got error message for the first code saying that, " unable to fetch some archives.... "

We really need all the text that was given in the terminal.
To do this highlight all the text in the terminal and right click and choose copy....then paste that back here...in your own reply of course.

---

