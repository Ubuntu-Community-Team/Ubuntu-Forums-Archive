---
title: "Help! Think I wrecked ubuntu!"
date: 2007-05-03
forum: General Help
---

### Post by matthewinuk on 2007-05-03
I used the command;

mount -o loop -t iso 9660 <source.iso> /home/matt

to mount a disc image to my home folder. I think there wasn't enough space (I know there wasn't) so now I cannot log on, although it will allow me onto a terminal to try and fix the problem, except I don't actually know how. Please help me someone! I don't konw how to unmount or how to go about deleting whatever file is in my home folder.

Many thanks

---

### Post by justinjstark on 2007-05-03
You could try

umount /home/matt

or

umount source.iso

---

