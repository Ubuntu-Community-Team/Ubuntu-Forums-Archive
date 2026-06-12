---
title: "Package Manager doesn't work."
date: 2007-10-12
forum: General Help
---

### Post by HelixAgent on 2007-10-12
Greetings everyone,

I come here with the following problem:
[IMG]http://i89.photobucket.com/albums/k240/Hikuroshi/error.png[/IMG]
I don't know why that is showing! I tried to install recordmydesktop and It apparently did but then this error comes out. Could somebody help me? Neither the Package Manager nor the Update Manager work.

---

### Post by por100pre1 on 2007-10-13
Try this (it will remove the package, unfortunately):

```
sudo dpkg --remove --force-remove-reinstreq recordmydesktop
```

Sorry for the delay.

---

### Post by HelixAgent on 2007-10-13
Thank you!! It worked perfectly! its nice to learn another command (LOL).
Thank you very much!

Helix.

---

### Post by por100pre1 on 2007-10-13
Typically, that command works for that specific issue. Please don't use it on any Synaptic issue, don't forget to ask if you need more help or just want to learn more. :)

---

### Post by HelixAgent on 2007-10-14
Haha ok! Thanks again. :D

---

