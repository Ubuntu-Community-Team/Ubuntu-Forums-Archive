---
title: "Can't drag and drop with mousepad - Xubuntu 14.04 - novatech laptop"
date: 2014-10-24
forum: General Help
---

### Post by Chrisinthedark on 2014-10-24
Hi,
just bought a pc without os and installed xubuntu 14.04. The touchpad wasn't working, but with this fix [http://ubuntuforums.org/showthread.php?t=2214287](http://ubuntuforums.org/showthread.php?t=2214287) by the user BennyHill seems to work.
A problem: I can't drag and drop, I mean, I push the left button of the touchpad with my thumb and move my index finger to move the object, but every time I leave my index finger from the touchpad, the object (i.e. a window or a scrollbar), goes to the very bottom of the screen.
This is annoying and it's driving me crazy. Is there any way I can fix it? Haven't I got the right driver?
Any help is very appreciated. Long live Ubuntu and Xfce.

Thanks

---

### Post by JKyleOKC on 2014-10-24
To drag and drop from a touchpad, I've always done it two-handed -- that is, press the left button with my left hand, and do the dragging with my right. This lets me release the button before removing my dragging finger from the pad, which has been the usual sequence as far back as I can remember... You might give this a try and see whether it makes a difference.

---

### Post by Chrisinthedark on 2014-10-24
To be honest, it seems to work almost fine if I do the action of dragging in this order: click the button with thumb, draggin whith index, release the thumb, release the index. Right to say that my previous pc, an HP Pavillion with Xubuntu 13.10 was working totally fine (in the order click-thumb, drag-index, release-index, release-thumb).

---

### Post by Chrisinthedark on 2014-10-24
...And now sometimes it stops working suddendly... and the only way to restore it, it's to press CTRL ALT DEL and log in again... please help... I'm going crazy!!!

---

### Post by davidongo on 2014-11-28
Yes, this random error seems to be associated to a lack of syncronization of the module psmouse, and it seems to be a Linux's Kernel bug for long time [more than five years, if you check the forums cited below]
The way to temporarily solve it [I know: we should go beyond, but this will work by now], are these couple of known commands:
[INDENT][SIZE=3]***sudo rmmod psmouse; sudo modprobe psmouse;***[/SIZE]
[/INDENT]
 Sources:
[http://xpapad.wordpress.com/2009/09/09/dealing-with-mouse-and-touchpad-freezes-in-linux/#comment-1182](http://xpapad.wordpress.com/2009/09/09/dealing-with-mouse-and-touchpad-freezes-in-linux/#comment-1182)
[http://askubuntu.com/questions/42093/reset-synaptics-touchpad/291588#291588](http://askubuntu.com/questions/42093/reset-synaptics-touchpad/291588#291588)



Regards, I hope it was useful
David López
[http://investigacionyprogramacion.com](http://investigacionyprogramacion.com)

---

