---
title: "bars at the top and bottom have vanished!"
date: 2008-06-04
forum: General Help
---

### Post by HuntMike79 on 2008-06-04
Today my nvidia fx5200 arrived. Great. I installed it and hook it up to my monitors. Dual displays under XP works like a charm. Awesome. Boot into Xubuntu, download and install restricted drivers. Exellent. Reboot and find it is only working on one screen and my bars at the top and bottom have vanished. Not good.

How can I fix this? I know how to bring terminal up but not much more...

---

### Post by fooman on 2008-06-04
try starting gnome-panels from a terminal with this:

```
gnome-panel &
```

---

### Post by HuntMike79 on 2008-06-04
> **fooman said:**
> try starting gnome-panels from a terminal with this:

```
gnome-panel &
```
I tried that and this is what I got:
> will@will-desktop:~$ gnome-panel &
[1] 5277
will@will-desktop:~$ The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found

[1]+  Exit 127                gnome-panel

Could this be why my bars have vanished?

---

### Post by plucky on 2008-06-04
HuntMike79,

You are running **Xubuntu** the command should be ```
xfce4-panel &
```

Good Luck

---

### Post by HuntMike79 on 2008-06-04
Yep, I'm running Xubuntu (sorry my 1st post didn't make this very clear). :o

I just typed that into terminal and it all magically appeared. :D I'm happy now, thanks. :)

---

### Post by fooman on 2008-06-04
oops,  didn't notice the xubuntu....sorry 'bout that.

---

