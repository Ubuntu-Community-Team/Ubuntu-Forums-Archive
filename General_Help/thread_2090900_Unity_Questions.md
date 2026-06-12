---
title: "Unity Questions"
date: 2012-12-03
forum: General Help
---

### Post by debodas on 2012-12-03
Well, I'm using unity as my desktop interface now.

Its not as bad as I thought, bad three things.

One is the workplace switcher - is there any way of moving this so it is stuck at the bottom of the dock, just above the Trash?

Two, is there any way to move the close, minimise, and maximise buttons so they are always at the top left of the screen, regardless whether the active window is taking up the whole screen or not? Given the options menu does this, it would be nice for the three buttons to stay there as well, no matter what the current window is sized to.

Finally, dash. I hate it. Any way of uninstalling it and replacing it with Gnome3 like application list?

Cheers.

---

### Post by LillyDragon on 2012-12-03
There's no sense in removing it, since it probably has a lot of GTK libraries and more already installed, saving you a lot of trouble while trying out another Window Manager.

If you want way more customization and little bloat, go with XFCE. It's a great Window Manager and you can change up the panels anyway you want, and even use images to texture the bars. A PPA for installing it on Precise is linked below.

[http://www.neowin.net/forum/topic/1076939-xfce-410-official-ppa-for-ubuntu-1204/](http://www.neowin.net/forum/topic/1076939-xfce-410-official-ppa-for-ubuntu-1204/)

---

### Post by NikTh on 2012-12-03
> **kingnick42 said:**
> One is the workplace switcher - is there any way of moving this so it is stuck at the bottom of the dock, just above the Trash?
Hi,
read this thread might help you => [**12.04 Unity - Can't get rid of Workspace Switcher Button](http://ubuntuforums.org/showthread.php?t=1970450)**

> **kingnick42 said:**
> Two, is there any way to move the close, minimise, and maximise buttons so they are always at the top left of the screen, regardless whether the active window is taking up the whole screen or not? Given the options menu does this, it would be nice for the three buttons to stay there as well, no matter what the current window is sized to. 
I don't know about this. But now that you mentioned it sounds as a good idea. You can report your ideas here => [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) . So fill an idea about the "global menu". :)

> **kingnick42 said:**
> Finally, dash. I hate it. Any way of uninstalling it and replacing it with Gnome3 like application list?


No , you have to install the whole gnome-shell environment if you don't want to use dash. If I understood you want Unity with gnome-shell like search.. no this cannot be happen (easy). 
But easy you can change desktop environment and use gnome-shell instead of Unity. 

Thanks

---

### Post by debodas on 2012-12-03
Well, sort of. I tried using Gnome3 as that is my preferred desktop interface, but it was hanging and lagging badly. I have another thread about that, but for now I'm stuck with unity. Dash and the workplace switcher are the two main annoyances.

I'll put forward my idea, it would be cool if it was implemented. I definitely think it would be a good thing.

Edit - I've submitted it.

---

### Post by bogan on 2012-12-04
Originally Posted by **kingnick42**                  
                 > Two, is there any way to move the close, minimise, and maximise buttons so they are always at the top left of the screen,Buttons to the right:```
 gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" 
```Buttons to the left:```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```Tkx to KansasNoob:[http://ubuntuforums.org/showthread.php?t=2018608&]("http://ubuntuforums.org/showthread.php?t=2018608&highlight=move+buttons+left")

Chao**, bogan.**

---

