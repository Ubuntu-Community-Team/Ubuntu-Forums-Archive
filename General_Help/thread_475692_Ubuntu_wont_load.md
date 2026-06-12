---
title: "Ubuntu wont load"
date: 2007-06-16
forum: General Help
---

### Post by gamemage on 2007-06-16
I tried installing Mountiso for ubuntu and being stupid I didnt see it was for kde only.

Since mountiso didnt work, I saw someone told us to type

```

sudo su
rm /bin/sh
ln -s /bin/sh /bin/bash

```

I did that. Now Ubuntu goes to the usplash but it doesnt load. Is there any way to fix this? I cant get into the terminal so I think I might have to reinstall which I really dont want to. Can someone please help?

---

### Post by gamemage on 2007-06-16
This is what I get when I press Alt-f2 on the usplash.

init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2420) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init:rc-default main process (2421) terminated with status 255

---

### Post by gamemage on 2007-06-16
bump

---

### Post by GuitarRocker2562 on 2007-06-16
dumb donkey, you deleted a critical part of the system, you may need to re-install. Then, learn to never ever ever type sudo (and sudo su is even worse) unless you know EXACTLY what it does.

BTW, all that command seems to do is to delete the sh program w/ bash, so you may not be able to launch anything, re-installing will be your best bet.

---

