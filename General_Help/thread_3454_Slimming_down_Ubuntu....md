---
title: "Slimming down Ubuntu..."
date: 2004-11-06
forum: General Help
---

### Post by shad0w on 2004-11-06
I have a p3 laptop with 192mb of ram, but most annoying, a 6GB HDD. I want to get rid of some of the apps that I know I'll never use to slim things down (like GIMP and some other stuff). The problem is, I can't uninstall any of them, ubuntu-desktop depends on them!

---

### Post by im_ka on 2004-11-06
install debfoster from universe and run it with sudo.

it'll group packages together and ask you if you wanna remove them. this way, you won't uninstall anything you need.

hth

---

### Post by Rancoras on 2004-11-06
Ubuntu-desktop is just a meta-package. A meta-package is used to create dependencies so that the installer only has to call one package to install the entire desktop. It's safe to remove it, your machine won't be damaged.

---

### Post by shad0w on 2004-11-06
[QUOTE=Rancoras]Ubuntu-desktop is just a meta-package. A meta-package is used to create dependencies so that the installer only has to call one package to install the entire desktop. It's safe to remove it, your machine won't be damaged.[/QUOTE]
Thanks for the great advice :mad: Gnome loads, and then now I just have a background, not toolbars or anything.

---

### Post by im_ka on 2004-11-06
i don't have "ubuntu-desktop" installed, and it's all good.
you're probably missing gnome-panel and such

try debfoster, it's a really cool tool to slim down your system.

---

### Post by Rancoras on 2004-11-06
[QUOTE=shad0w]Thanks for the great advice :mad: Gnome loads, and then now I just have a background, not toolbars or anything.[/QUOTE]

I assume you are blaming me for this.  Well, I know what worked for me and what has worked for many others on the board.  I'm sure you made sure no gnome-* packages were going to be uninstalled right?

---

### Post by shad0w on 2004-11-06
[QUOTE=Rancoras]I assume you are blaming me for this.  Well, I know what worked for me and what has worked for many others on the board.  I'm sure you made sure no gnome-* packages were going to be uninstalled right?[/QUOTE]
Nvm, I fixed it :p

Anyway, I can't seem to find debfoster and I have the universe repository checked in synaptics :(

Another quick question: I'm trying to reduce memory usage and I've already done stuff with the themes and things, but why is it that so many apps use so much memory? For example, the trash can applet uses nearly 30 megs! Why does it need so much memory? It's not even doing anything!

---

### Post by im_ka on 2004-11-06
have you tried xfce4?

it's "gnome light"

---

### Post by shad0w on 2004-11-06
[QUOTE=im_ka]have you tried xfce4?

it's "gnome light"[/QUOTE]
I can't seem to find it in universe...I followed the wiki and it is enabled.

---

### Post by im_ka on 2004-11-06
[QUOTE=shad0w]I can't seem to find it in universe...I followed the wiki and it is enabled.[/QUOTE]

did you run
```
 sudo apt-get update
```
?

that might help you to find debfoster as well

---

