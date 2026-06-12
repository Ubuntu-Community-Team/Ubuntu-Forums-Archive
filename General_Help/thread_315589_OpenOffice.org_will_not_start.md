---
title: "OpenOffice.org will not start"
date: 2006-12-09
forum: General Help
---

### Post by phatzmb on 2006-12-09
When I try to load OpenOffice it just goes to the spashscreen and then quits. This happens with all the programs.

When i try and load it from the terminal this is what i get:

```

hr@hubuntu:~$ ooffice -writer
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: /usr/lib/openoffice/program/libtk680li.so: unexpected PLT reloc type 0x00

** (process:5526): WARNING **: Unknown error forking main binary / abnormal early exit ...
hr@hubuntu:~$ 

```

Any ideas?

---

### Post by taurus on 2006-12-09
Are you using Dapper or Edgy and this happens recently or this is the first time you run OpenOffice?

---

### Post by phatzmb on 2006-12-09
I'm using Edgy. I did successfully run OpenOffice before, but that was using a different video card. I think with the GeForce 6200 I'm using now I previously only ran the setup, I don't remember actually using the writer.

I have tried reinstalling the OpenOffice multi-package in Synaptic, but nothing has changed.

---

### Post by phatzmb on 2006-12-09
bump

---

### Post by phatzmb on 2006-12-11
I wonder if this is related to another problem I just noticed:

emacs will not display any text other than box characters. instead of all the text you normally see, including the menus, there are only boxes.

---

### Post by phatzmb on 2006-12-16
another bump... still hoping this problem can be solved.

after trying fedora core 6 i reinstalled ubuntu. openoffice still wouldn't start. 
emacs was fine for a while but now its back to the little squares. it must be something i installed.

---

