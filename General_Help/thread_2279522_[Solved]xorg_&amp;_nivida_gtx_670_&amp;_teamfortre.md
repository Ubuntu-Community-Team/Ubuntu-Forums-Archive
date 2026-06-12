---
title: "[Solved]xorg &amp; nivida gtx 670 &amp; teamfortress"
date: 2015-05-24
forum: General Help
---

### Post by patrikmellq on 2015-05-24
Hello i install Steam and TeamFortress - it works fine to play with opengl.
But i have not install any specific drivers for my nivida card gtx 670 - does xorg use it with default driver?

Cheers

---

### Post by Vladlenin5000 on 2015-05-24
The default is the open source driver *nouveau*.

---

### Post by patrikmellq on 2015-05-24
Thanks - does [I]nouveau use my nivida gtx 670 card or does it use the mother-boards grhapics ...

Cheers
[/I]

---

### Post by Vladlenin5000 on 2015-05-24
Sorry for the late reply... I've been around but somehow missed your last post.

*Nouveau* is for nvidia and nvidia only. All Intel, the most common integrated chips, works with open source drivers.

---

### Post by patrikmellq on 2015-05-25
> **Vladlenin5000 said:**
> Sorry for the late reply... I've been around but somehow missed your last post.

*Nouveau* is for nvidia and nvidia only. All Intel, the most common integrated chips, works with open source drivers.

Thanks for your help - Nouveau did not give me a sharp and smooth experience - so i install Nvidia 331 recommended with OpenGL so could run Steam and TF2.
I solve it and find a simple solution for the 32 libary with my Ubuntu 64 bit: [http://ubuntuforums.org/showthread.php?t=2279564](http://ubuntuforums.org/showthread.php?t=2279564)

Put the link here is some one search for same issue.

Cheers

---

### Post by Vladlenin5000 on 2015-05-25
Very nice and thank you for your effort in adding the complementary link.

You can also use the thread tools in your first post to mark this one as solved so other can benefit.

Happy Ubuntuing ;)

---

