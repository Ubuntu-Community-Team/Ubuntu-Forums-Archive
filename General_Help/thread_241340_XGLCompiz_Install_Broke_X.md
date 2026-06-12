---
title: "XGL/Compiz Install Broke X"
date: 2006-08-22
forum: General Help
---

### Post by rowanparker on 2006-08-22
Hey,
I was using [this]("http://www.compiz.net/viewtopic.php?id=389") tutorial to install XGL/Compiz. And I followed the "second" tutorial and then rebooted and X failed to start.

Does anyone know why this is happening and how to get X to start so I can use my computer (I don't class Windows as using)?

Thanks, Rowan.

---

### Post by slimdog360 on 2006-08-22
I can tell you what I done when I uninstalled XGL/compiz, but note that I didnt use the same tutorial as you, the one I used was more similar to the first one on that page.

first I uninstalled these packages using sudo aptitude remove...
compiz
compiz-gnome
libglitz-glx1
libglitz1
libxcomposite1
xserver-xgl

then I had to change my gdm.conf-custom file to its original state, but I noticed in the tutorial you used you didnt change this in the first place.


That was it, I got my old desktop back. So unless someone else knows how to fix it I'd suggest you just delete the files that you installed which were

(from your tutorial page)
compiz 
xserver-xgl 
libgl1-mesa 
xserver-xorg 
libglitz-glx1
compiz-gnome

and you should also delete the startup scripts that you made. Of course once that is done you should delete the extra repositories that were added.

---

### Post by frodon on 2006-08-22
There's a bug with the latest xserver update, see this thread for details : 
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by frup on 2006-08-22
[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

thats a really nice tutorial which shouldnt break x

---

### Post by rowanparker on 2006-08-22
I uninstalled what you said and rebooted and it still failed to start X.

Is there anyway I can completly remove X and start again? Or is there something else I should do?

---

### Post by abelthorne on 2006-08-22
> **rowanparker said:**
> I uninstalled what you said and rebooted and it still failed to start X.

Is there anyway I can completly remove X and start again? Or is there something else I should do?

If you upgraded (maybe accidentally) to the latest Xorg update that is still in the repositories, it is broken and you'll have to install the previous version.

---

### Post by rowanparker on 2006-08-22
Im doing what frodon said.

---

### Post by rowanparker on 2006-08-22
It worked (I'm writing this on Ubuntu).

Thank you people!

---

