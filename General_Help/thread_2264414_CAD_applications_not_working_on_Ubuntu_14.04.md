---
title: "CAD applications not working on Ubuntu 14.04"
date: 2015-02-07
forum: General Help
---

### Post by patocardo on 2015-02-07
Hello.

I've just moved from ubuntu 10 (32 bits) to ubuntu 14 (64 bits) because of Draftsight, which now is only 64b. Once I installed all the system and programs, I realize that Draftsight can barely open files and move the pointer.

I decided to install LibreCAD and TeighaFileConverter to read DWG files. The result was the same, too slow to do anything.

So, I tested SageCAD, but this time the application crashes when I open any file.

What is happening and what can I do? Thank you in advance

---

### Post by Impavidus on 2015-02-07
Could you show us the specs of your hardware? If you used 10.something 32 bits before, it might be weaker. 64 bit needs more memory to do the same task as 32 bit and being sluggish and crashing sometimes often indicates lack of ram. It may also be that you don't have the right graphics driver installed for the new kernel you now use.

---

### Post by patocardo on 2015-02-13
Impavidus, thanks for answering.
    If you are right, I don't know why did I upgrade. But it sounds correct, all the system is slower now.
I have 2GB Ram, with a Geniune Interl CPU 2160 @ 1.80GHz x 2, and a GeForce 210/PCle/SSE2 graphic card.

---

### Post by v3.xx on 2015-02-13
Since you have ubuntu installed, you could try adding a lighter desktop environment to it.
```
sudo apt-get install gnome-panel
```
At the login screen choose Flashback (metacity) desktop.

---

