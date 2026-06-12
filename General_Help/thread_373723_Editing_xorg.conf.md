---
title: "Editing xorg.conf?"
date: 2007-03-01
forum: General Help
---

### Post by skysong on 2007-03-01
I've been following the instructions found [here]("http://ubuntuforums.org/showthread.php?t=25151") to make my Wacom Tablet work with Linux/Gimp. 

I got as far editing xorg.conf and got stuck.  I've been using VIM (is that a good choice?) and can't get it to save the changes. 

Can anyone give a noob some advice? Thanks! (Or let me know if I need to give more information? Or point me to where I should be asking this question? Or to where it's been answered? Please?)

-Skysong

---

### Post by 23meg on 2007-03-01
You'll need to use sudo / gksudo, since as a regular user you don't have write access to xorg.conf.

```
gksudo gedit /etc/X11/xorg.conf
```

More information:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by sgstarling on 2007-03-01
For now, I'd go with what 23meg said.  (using gedit, intead of vim)

However, if you are interested in learning more about vim (GREAT editor for hard core editors...) try this tutorial: [vim tutorial]("http://www.vi-improved.org/tutorial.php"). I found it to be very educational AND entertaining.

---

### Post by skysong on 2007-03-01
Thanks for all your help!

It turns out I just needed to use sudo. 

Thanks again!

---

