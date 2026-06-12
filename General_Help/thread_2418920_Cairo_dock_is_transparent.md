---
title: "Cairo dock is transparent"
date: 2019-05-13
forum: General Help
---

### Post by jeeper74 on 2019-05-13
Not sure what I did. My cairo dock has gone nearly completely transparent, and I can only see it against a black background. The task menu when open shows up fine, overtop of any open windows, but not the dock itself. 

I am using Ubuntu 18.04 Gnome and Cairo-dock 3.4.1 

I have changed themes, and tried about every setting that looked even remotely connected with how the dock looks, no change.
I have tried uninstalling it and re-installing, no luck.
I tried apt-get purge and reinstalling, still no change.

A short video of my problem.
[https://youtu.be/YhVNenKKSIc](https://youtu.be/YhVNenKKSIc)

Anyone have the know how to tell me what to do to make it work like it used to again?

---

### Post by Xian on 2019-05-13
I tried a few configuration options but could not duplicate the dock's behavior in your video. 

For myself I would rename the configuration folder at $HOME/.config/cairo-dock. 

Then logout/login to the desktop to what should be a default setup of cairo-dock.

---

### Post by jeeper74 on 2019-05-14
I will give that a try, thanks

---

### Post by jeeper74 on 2019-05-14
So that did not fix it. I changed the folder name and rebooted. It did change my appearance of the dock, icons and spacing and such, but no change on the transparency issue.

---

### Post by CatKiller on 2019-05-14
Windows can't generally make themselves transparent; they ask the window manager to do it for them.

It sounds like you've got another setting somewhere that's making your dock transparent. I don't use Gnome, so I couldn't tell you what that setting would be.

Compiz' transparency shortcut was Alt-scrollwheel, I think, so whatever you've got that's giving you transparency might use the same combination.

---

### Post by jeeper74 on 2019-05-14
thank you CatKiller, that set me on the right path. OpenGL with my graphics card and Cairo was all a no go. I switched Cairo's "render" method ( don't remember exactly what they called it...) to not use OpenGL and boom, all the stars aligned and angles were singing and all that.

---

