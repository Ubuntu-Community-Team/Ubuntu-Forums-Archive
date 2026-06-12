---
title: "System slows down during startup?"
date: 2007-03-05
forum: General Help
---

### Post by agentstewie on 2007-03-05
I have some wierd problem...
After sucessfully installing beryl with aiglx on intel 945gm graphics, ubuntu gets stuck at this screen for quite some time, even though i could ignore it, I prefer to get the error fixed.

Since it might be beryl, i quit out of beryl and i launched terminal and launched it by typing 'beryl-manager'  and this is what came up
```
rbehera@rbehera-laptop:~$ beryl-manager 
rbehera@rbehera-laptop:~$ libGL warning: 3D driver claims to not support visual 0x5b
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLXrbehera@rbehera-laptop:~$ beryl-manager 
rbehera@rbehera-laptop:~$ libGL warning: 3D driver claims to not support visual 0x5b
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x5b
Reloading options



Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x5b
Reloading options


```
and it gets stuck there.
I think it has to do something with "libGL warning: 3D driver claims to not support visual 0x5b"
any clues?
screeenshot attached for those not sure where im getting stuck at

---

### Post by agentstewie on 2007-03-08
bump

---

