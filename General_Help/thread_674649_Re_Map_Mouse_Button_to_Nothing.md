---
title: "Re Map Mouse Button to Nothing"
date: 2008-01-21
forum: General Help
---

### Post by dethredic on 2008-01-21
Hi

I have a Logitech G5 mouse and I am using btnx. To make it work better, I need to make one of my buttons not do anything. Is there any way I can do this?

---

### Post by erpo on 2008-01-22
> **dethredic said:**
> Hi

I have a Logitech G5 mouse and I am using btnx. To make it work better, I need to make one of my buttons not do anything. Is there any way I can do this?

What have you already tried?

---

### Post by dethredic on 2008-01-22
nothing, I dono't know where to start.

---

### Post by p_quarles on 2008-01-22
To configure a multi-button mouse, you'll need to edit /etc/X11/xorg.conf and your Xmodmap settings. The latter is usually located in ~/.Xmodmap, which will only affect settings for the user whose home dir is altered. Alternatively, you can create a file /etc/X11/Xmodmap. That will change settings for all users. 

It's not the easiest thing in the world, and modifying xorg.conf always comes with risks (be sure to back it up first!). But, here's a guide:
[http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons](http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons)

---

### Post by dethredic on 2008-01-26
I don't see where I can re map them to nothing. Just to other buttons.

---

