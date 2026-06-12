---
title: "Root privileges from a right-click menu"
date: 2008-05-19
forum: General Help
---

### Post by Jackelope on 2008-05-19
I just tried the new Linux Mint 5 Beta. I'm sticking with Ubuntu Hardy, but one thing I really liked about Mint 5 was the ability to open any folder as root from a right-click menu. I know it's dangerous, but it made editing my Grub files a lot easier. Is there a way to install a feature like this in Ubuntu? Thanks for the help!

---

### Post by sardion on 2008-05-20
This is not the safest thing to do.  That said,

you can make any command run as root in gnome by putting gksudo in front of it.

So, edit the right click menu and add a command "gksudo gedit", that will let you edit files as root.

---

### Post by bingoUV on 2008-05-20
[http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/](http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/)

This is not even dangerous. It has the additional hassle of entering password every 5 minutes. I don't know if that is so in Mint.

If you use PolicyKit, it should be even safer but I am yet to try it so cannot give a how-to.

---

### Post by noynac on 2008-05-20
> **Jackelope said:**
> I just tried the new Linux Mint 5 Beta. I'm sticking with Ubuntu Hardy, but one thing I really liked about Mint 5 was the ability to open any folder as root from a right-click menu. I know it's dangerous, but it made editing my Grub files a lot easier. Is there a way to install a feature like this in Ubuntu? Thanks for the help!

Another option is to install Nautilus Actions from synaptic and import the "open in gedit as root" configuration. You then right-click on the file and select edit as root. 

[http://www.grumz.net/?q=node/212&PHPSESSID=1a045bc491929e6a60253c6d43da55b3](http://www.grumz.net/?q=node/212&PHPSESSID=1a045bc491929e6a60253c6d43da55b3)

For me, an even easier solution is to create alias's in your .bashrc file for important configuration files, although that's a bit off-topic.

---

### Post by Jackelope on 2008-05-20
Thanks for the help!

---

### Post by chrisccoulson on 2008-05-20
Another option:
```
sudo apt-get install nautilus-gksu
```

---

