---
title: "mini.iso + lubuntu + xrdp"
date: 2014-07-12
forum: General Help
---

### Post by hbc2 on 2014-07-12
Hi,

I installed from the 14.04 mini.iso and in the list of choices I chose lubuntu desktop.  After booting into the desktop I opened a terminal and installed xrdp.

When I connect to the linux machine from windows using remote desktop I get a grey screen with an X mouse cursor after logging in.

I found the following page (link below) and edited [COLOR=#666666][FONT=Consolas]etc/xrdp/startwm.sh [/FONT][/COLOR]by adding **. /usr/bin/startlxde **

However, when I use the terminal and cd into **/usr/bin/ **and then do an ls the file **startlxde** is not there (but startx is).

Any idea how I can get this working from windows remote desktop?

This is the link I mentioned above:
[http://www.blime.com/2014/xrdp-remote-desktop-on-lubuntu-14-04/](http://www.blime.com/2014/xrdp-remote-desktop-on-lubuntu-14-04/)

---

### Post by Toz on 2014-07-12
Not a lubuntu user, but...
```
$ apt-file search startlxde
lxde-common: /usr/bin/startlxde
lxde-common: /usr/share/man/man1/startlxde.1.gz

```

"/usr/bin/startlxde" is from the **lxde-common** package - you'll need to install that package if you want to use startlxde.

---

### Post by ibjsb4 on 2014-07-12
I am not a windows user, but I do use startx.  So I ask more than tell; isn't xinitrc still required for this to work?

[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

---

