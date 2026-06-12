---
title: "tar.bz2,,how do i install"
date: 2007-03-11
forum: General Help
---

### Post by STREETURCHINE on 2007-03-11
i am trying to install a tar.bz2 file
and i am not succeding,i am doing this to learn how ,i follow the instructions and it just dont work or i cant understand how to make iy work one or the outher.

anyway i have untared it ,cd into the directory and i am stuck here

  ```
rex@rex-desktop:~$ tar xvjf kiba.tar.bz2
kiba-dock/
kiba-dock/CVS/
kiba-dock/CVS/Root
kiba-dock/CVS/Repository
kiba-dock/CVS/Entries
kiba-dock/CVS/Template
kiba-dock/bin/
kiba-dock/bin/CVS/
kiba-dock/bin/CVS/Root
kiba-dock/bin/CVS/Repository
kiba-dock/bin/CVS/Entries
kiba-dock/bin/CVS/Template
kiba-dock/NEWS
kiba-dock/TODO
kiba-dock/dock/
kiba-dock/dock/CVS/
kiba-dock/dock/CVS/Root
kiba-dock/dock/CVS/Repository
kiba-dock/dock/CVS/Entries
kiba-dock/dock/CVS/Template
kiba-dock/dock/kiba-window.c
kiba-dock/dock/kiba-window.h
kiba-dock/dock/kiba-akamaru.c
kiba-dock/dock/kiba-akamaru.h
kiba-dock/dock/kiba-dock.c
kiba-dock/dock/kiba-dock.h
kiba-dock/dock/kiba-render.c
kiba-dock/dock/kiba-render.h
kiba-dock/dock/kiba-gconf.c
kiba-dock/dock/kiba-gconf.h
kiba-dock/dock/Makefile.am
kiba-dock/dock/kiba-launcher.c
kiba-dock/dock/kiba-launcher.h
kiba-dock/dock/kiba-geometry.c
kiba-dock/dock/kiba-geometry.h
kiba-dock/dock/kiba-events.c
kiba-dock/dock/kiba-events.h
kiba-dock/files/
kiba-dock/files/CVS/
kiba-dock/files/CVS/Root
kiba-dock/files/CVS/Repository
kiba-dock/files/CVS/Entries
kiba-dock/files/CVS/Template
kiba-dock/files/Makefile.am
kiba-dock/files/kiba.schemas
kiba-dock/files/SimpleGladeApp.py
kiba-dock/icons/
kiba-dock/icons/CVS/
kiba-dock/icons/CVS/Root
kiba-dock/icons/CVS/Repository
kiba-dock/icons/CVS/Entries
kiba-dock/icons/CVS/Template
kiba-dock/icons/kiba_16.png
kiba-dock/icons/kiba_24.png
kiba-dock/icons/kiba_48.png
kiba-dock/icons/kiba_128.png
kiba-dock/icons/kiba_64.png
kiba-dock/icons/Makefile.am
kiba-dock/utils/
kiba-dock/utils/CVS/
kiba-dock/utils/CVS/Root
kiba-dock/utils/CVS/Repository
kiba-dock/utils/CVS/Entries
kiba-dock/utils/CVS/Template
kiba-dock/utils/kiba-systray.py
kiba-dock/utils/kiba-icons.glade
kiba-dock/utils/kiba-icon-editor.py
kiba-dock/utils/Makefile.am
kiba-dock/utils/populate-dock.sh
kiba-dock/README
kiba-dock/configure.in
kiba-dock/autogen.sh
kiba-dock/Makefile.am
kiba-dock/akamaru/
kiba-dock/akamaru/CVS/
kiba-dock/akamaru/CVS/Root
kiba-dock/akamaru/CVS/Repository
kiba-dock/akamaru/CVS/Entries
kiba-dock/akamaru/CVS/Template
kiba-dock/akamaru/Makefile.am
kiba-dock/akamaru/main.c
kiba-dock/akamaru/akamaru.c
kiba-dock/akamaru/akamaru.h
kiba-dock/AUTHORS
kiba-dock/gset-kiba/
kiba-dock/gset-kiba/CVS/
kiba-dock/gset-kiba/CVS/Root
kiba-dock/gset-kiba/CVS/Repository
kiba-dock/gset-kiba/CVS/Entries
kiba-dock/gset-kiba/CVS/Template
kiba-dock/gset-kiba/gset-kiba.c
kiba-dock/gset-kiba/Makefile.am
kiba-dock/gset-kiba/gset-kiba.glade
kiba-dock/ChangeLog
kiba-dock/COPYING
rex@rex-desktop:~$ cd kiba-dock
rex@rex-desktop:~/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.
rex@rex-desktop:~/kiba-dock$ ./install
bash: ./install: No such file or directory
rex@rex-desktop:~/kiba-dock$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
rex@rex-desktop:~/kiba-dock$


```

as you can see i have tried a few ideas but no tshirt.

thanks for any advice

---

### Post by taurus on 2007-03-11
```
./autogen.sh
./configure
make
sudo make install
-or-
sudo aptitude install checkinstall
sudo checkinstall
```
Or read the README.

```
more README
```

---

### Post by STREETURCHINE on 2007-03-11
thanks again ,i did find the read me didnt realy understand it the first time so i read it again and found the bit i missed.it seemed ti install ok but it wont work.

it was a rpm(so i used alien for the first time) i am just trying differant ways to install stuff.

learning how to install differant packages in linux would have to be the hardest thing i have tackled so far.

anyway taurus thanks,but expect to hear from me again still a few to try,,:lolflag:

---

### Post by taurus on 2007-03-11
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

