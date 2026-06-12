---
title: "Problems Mounting CD Image"
date: 2007-03-05
forum: General Help
---

### Post by poebae on 2007-03-05
Whenever I try to mount a CD image, the mount command gives me the error message:

"mount: not a directory"

```

sudo modprobe loop
sudo mount example.iso /media/example/ -t iso9660 -r -o loop -v

mount: going to use the loop device /dev/loop0
mount: Not a directory
```

Can anyone help me fix this? I've tried using things like cdemu, but since they ultimately boil down to using the mount command anyway, I always encounter the same problem.

---

### Post by taurus on 2007-03-05
Try something like

```
sudo mount -t iso9660 -o loop sample.iso /media/example
```

---

### Post by Arisna on 2007-03-05
I'm also fairly sure /media/example, for this case, needs to exist and be a directory for this to work.

---

### Post by poebae on 2007-03-05
Thanks for the help, but I still get the same error message:

```
mount: going to use the loop device /dev/loop0
mount: Not a directory
```

I've created the relevant directory (/media/example), so it seems to be referring to the fact that /dev/loop0 isn't a directory, which is true.

---

### Post by taurus on 2007-03-05
Which release are you running right now and which kernel are you using?

---

### Post by poebae on 2007-03-06
I don't have access to my machine at the moment, so I'm not sure which kernel I'm using, but I'm running Edgy 6.10

---

### Post by poebae on 2007-03-07
I'm running 2.7.17-11-386

---

