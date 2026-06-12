---
title: "usr/bin/sh does not exist"
date: 2007-05-13
forum: General Help
---

### Post by Kazur on 2007-05-13
Hello there!

I have compiled a program, Panda3d. To run programs in panda, I use this script:

[PHP]
#!/usr/bin/sh

PATH=/home/matt/software/Panda3D-1.3.2/usr/bin:$PATH
export PATH

LD_LIBRARY_PATH=/home/matt/software/Panda3D-1.3.2/usr/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH

PYTHONPATH=/home/matt/software/Panda3D-1.3.2/usr/share/panda3d:$PYTHONPATH
export PYTHONPATH 
[/PHP]

When I run the script, I get this error:
bash: ./script: /usr/bin/sh: bad interpreter: No such file or directory

I have checked /usr/bin/, and there is no "sh" file there. Do you know how I can fix this, or alternatively install "sh"?

I'm using Ubuntu 7.04.

---

### Post by heimo on 2007-05-13
Try /bin/sh

---

### Post by rich.bradshaw on 2007-05-13
ln -s /usr/bin/sh /bin/sh

---

