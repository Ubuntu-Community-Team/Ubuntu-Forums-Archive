---
title: "UNetbootin not starting"
date: 2017-10-27
forum: General Help
---

### Post by 1jarwolf on 2017-10-27
If I run UNetbootin, it asks for my sudo password, I insert it and then nothing happens afterwards. If I use the terminal and type in "unetbootin" I get "root@unknown:/home/jared# unetbootin[COLOR=#ff0000]No protocol specified[/COLOR]
[COLOR=#ff0000]unetbootin: cannot connect to X server :0[/COLOR]"

---

### Post by vmalep on 2017-11-06
Same problem for me. And it happens also with gparted. It is linked to Wayland as I understood...

See for example: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1652282](https://bugs.launchpad.net/ubuntu-gnome/+bug/1652282)

---

### Post by VMC on 2017-11-06
'gparted' always will since it needs to take control of your drives/partitions.

---

### Post by #&amp;thj^% on 2017-11-06
About 6 months ago I found this to work:
Loged in as normal user then run:

```
xhost local:root
```

Then with sudo:

```
sudo QT_X11_NO_MITSHM=1 /usr/bin/unetbootin 
```

And just this may work..It used to anyway.
 
```
xhost +local
```
Good Luck and I hope someone else can confirm this.
**Still not sure how safe this is...but It will only last the current logged in session.**

---

