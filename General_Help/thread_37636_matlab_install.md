---
title: "matlab install"
date: 2005-05-27
forum: General Help
---

### Post by iakie on 2005-05-27
I was trying to install matlab from CD. for some reason, bash keep saying that permission denied, even though i was doing it under root. it seems that the install script on CD's permission is set to 555. anyone have a clue?

some code dump:

```

root@PromiseLand:/media/cdrom # ls
install               inst_doc.pdf  mac_install_guide.pdf  update
InstallForMacOSX.app  license.txt   readme.txt             utils
root@PromiseLand:/media/cdrom # ./install
bash: ./install: /bin/sh: bad interpreter: Permission denied
root@PromiseLand:/media/cdrom #
```

---

### Post by hondje on 2005-05-28
[QUOTE=iakie]I was trying to install matlab from CD. for some reason, bash keep saying that permission denied, even though i was doing it under root. it seems that the install script on CD's permission is set to 555. anyone have a clue?

some code dump:

```

root@PromiseLand:/media/cdrom # ls
install               inst_doc.pdf  mac_install_guide.pdf  update
InstallForMacOSX.app  license.txt   readme.txt             utils
root@PromiseLand:/media/cdrom # ./install
bash: ./install: /bin/sh: bad interpreter: Permission denied
root@PromiseLand:/media/cdrom #
```[/QUOTE]

I have had the same problem in Sarge, Sid, and Ubuntu.  At one time I thought it was related to mounting the disk noexec, but that doesn't fix it.  What I do is cp the disk to $HOME/tmp and run the installer script from there (as root or with sudo), and it runs without a hiccup.  

If you ever figure out how to get openGL and nvidia cards working with it, I'd love to know :)

---

### Post by lorap on 2005-05-30
my dear friend!
i've successfully installed it going through a lot of troubles!
but as i've seen at the end of the process, it wasn't too difficult!
this's my mail:
[email]prianfamily@gmail.com[/email]
write me that you're ready to begin and i'll write you the manual
pavel

p.s.:
you probably have a crack so you'll need to solve some equations to install it :-)

---

### Post by gp123 on 2005-06-06
I had the same problem and found the solution here:

[http://www.mathworks.com/support/solutions/data/1-184PH.html?solution=1-184PH](http://www.mathworks.com/support/solutions/data/1-184PH.html?solution=1-184PH)

It has to do with how you mount the CD.  I had to use the command:

mount -t iso9660 /dev/hdc /cdrom

and then it worked fine.

---

