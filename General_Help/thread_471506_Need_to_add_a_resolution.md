---
title: "Need to add a resolution"
date: 2007-06-12
forum: General Help
---

### Post by Codio on 2007-06-12
I have a 19" widescreen monitor, and when I had windows (windows died on me so I switched to ubuntu), I ran it on 1440x900. I know I have to edit xorg.conf in order to add in this resolution. However, I need to be in root to save it, and I just flat out can't remember how to do that. 

I was told by a friend that he 'thinks' I just have to add in "1440x900" to the list of resolutions, but he wasn't sure. Is this really all there is to it? 

Any help would be greatly appreciated, and many thanks in advance. 

-Codi

---

### Post by anaconda on 2007-06-12
open the editor with sudo command.

eg. type in terminal:
sudo nano /etc/X11/xorg.conf

will open the file with root (admin) rights.

And adding the resolution to that file should work.

I usually change the resolution with:
nvidia-settings
but that is because I have an nvidia display card., and I have installed the drivers to it..

---

### Post by CocoAUS on 2007-06-12
I suggest checking here:

[http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution](http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution)

---

