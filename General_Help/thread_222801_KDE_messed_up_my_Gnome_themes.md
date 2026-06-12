---
title: "KDE messed up my Gnome themes"
date: 2006-07-25
forum: General Help
---

### Post by ketsugi on 2006-07-25
After using aptitude to install and then later remove kubuntu-desktop, I found that in Gnome all my GTK themes had been messed up. Now it seems that most of them have been modified to match my current GTK theme, and also that the font size in the gnome panel and certain applications has been made bigger and cannot be modified from the Font system preference control.

How do I undo the damage done to my themes, and reduce my panel font size again?

---

### Post by kpkeerthi on 2006-07-25
I had the same problem a while ago. I had to completely remove ubuntu-desktop and reinstall it to get away from the problem. Yes... it was laborious. But I had no option.

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

### Post by aysiu on 2006-07-25
[This thread](http://www.ubuntuforums.org/showthread.php?t=161434) may help you out.

---

### Post by Jucato on 2006-07-25
I also had that problem, and solved it the way that was described in the thread aysiu linked to. Unfortunately, I had to figure that one out myself for a few hours, since I didn't see that thread. :D

---

### Post by ketsugi on 2006-07-25
That method didn't quite work since I'd already uninstalled kubuntu-desktop. The kcontrol package was still left behind for some reason, but when I ran it, I couldn't find the option for Gtk themes (probably because I was using Gnome).

But what did work was just deleting the ~/.gtkrc-2.0 file.

Thanks for the tips.

---

