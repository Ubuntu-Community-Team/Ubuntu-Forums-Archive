---
title: "mount: cant fine /home/brett........... HELP"
date: 2008-06-11
forum: General Help
---

### Post by Vrekk on 2008-06-11
Ok so i am trying to mount a virtual drive.  Well normaly i would go ```
sudo mount -o loop '/home/brett/desktop/HALO.iso'
```(halo is the cd i am trying to mount and my name is brett) but i get a
```
Mount: can't fine /home/brett/Desktop/HALO/iso in /ect/fstab or /ecct.mtab
``` can any one help! i will do that exact same code with my desktop and it works great, (this is the laptop)

---

### Post by sdennie on 2008-06-11
You need to include a mount point.  For example, the following should work:

```

mkdir ~/Desktop/Halo
mount -o loop /home/brett/Desktop/HALO.iso /home/brett/Desktop/Halo

```

That will mount the iso on your desktop but assumes the iso is located in /home/brett/Desktop.

---

### Post by Vrekk on 2008-06-11
oh dang i feel stupid now i forgot to add the mount point.  Thanks anyways vor

---

