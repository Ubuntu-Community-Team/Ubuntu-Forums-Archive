---
title: "Beryl Causing Menu/Title bar on windows"
date: 2007-04-29
forum: General Help
---

### Post by dann1029 on 2007-04-29
I just reinstalled Feisty and then Beryl, but whenever I go to start beryl, my title bar on all my windows disappear making it impossible to move windows around and all that other stuff. Help would be much appreciated.

---

### Post by m.musashi on 2007-04-29
See if anything in this thread proves useful.

[http://ubuntuforums.org/showthread.php?t=414103](http://ubuntuforums.org/showthread.php?t=414103)

---

### Post by barberboy on 2007-05-06
Greetings dann1029.

I was having the problem you described and found a fix [here]("http://www.linuxquestions.org/questions/showthread.php?p=2590815#post2590815") which is:

Backup your xorg config file:
```
sudo cp /etc/X11/xorg.conf xorg.conf.backup
```

Open your xorg.config for editing:
```
sudo gedit /etc/X11/xorg.conf
```

In the "Screen" section, add the following two options:
```
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
```

Then restart the X server with **Ctrl-Alt-Backspace**

That fix worked for me. Hope it helps.

---

