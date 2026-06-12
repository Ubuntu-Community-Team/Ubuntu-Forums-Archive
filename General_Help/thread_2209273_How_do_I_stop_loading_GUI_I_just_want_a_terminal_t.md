---
title: "How do I stop loading GUI I just want a terminal to load instead off gui?"
date: 2014-03-04
forum: General Help
---

### Post by andreamillspaugh on 2014-03-04
Hi, How do I stop loading GUI I just want a terminal to load at startup instead of the GUI, I just want the you know the black screen and a promed as root.

---

### Post by Bashing-om on 2014-03-04
andreamillspaugh; Hi !

Single instance : from grub menu, 'e' key for edit mode -> boot parameters screen; arrow down and across, and replace the terms "quiet splash" with the term text; key combo ctl+x to continue the boot process to a terminal log in.

Persistent: edit the file /etc/default/grub ( make a backup prior to doing any editing in any file) find those terms quiet splash, replace with the term text. save the file, exit back to terminal and ->
propagate that change to the other boot control files by issuing terminal command:
```

sudo update-grub

```
reboot to see the effect:
```

sudo shutdown - r now

```


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by lildigiman on 2014-03-04
Bashing-om, seems you misread the question.

Seems like what andreamillspaugh is looking for is here: [http://ubuntuforums.org/showthread.php?t=1661065](http://ubuntuforums.org/showthread.php?t=1661065)

---

