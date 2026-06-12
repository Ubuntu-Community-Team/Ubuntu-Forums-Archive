---
title: "compiz works, but not with gdm"
date: 2008-04-28
forum: General Help
---

### Post by renauldo on 2008-04-28
As long as I start an xsession with something other than GDM, I can get effects (compiz) to start.  If I start via GDM, I get the errors about DRI not being loaded.

I can't see how this can be -- asfaict, GDM is using the same /etc/X11/xorg.conf as xinit and friends...  Anyone have any idea why GDM is making things crazy?

Thanks,
Renauldo

---

### Post by renauldo on 2008-05-06
I just upgraded kernel and nvidia drivers that became available yesterday, and still have this issue: in order to compiz|DRI to work, I have to '/etc/init.d/gdm stop', 'xinit', and then in the controlling term startup 'gnome-session'.

Why would this not work when X is started from gdm?  I don't see any crazy strings in the args gdm passes to X (in ps axf).

---

### Post by renauldo on 2008-07-24
output from compiz-check via gdm gnome session:

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7100 GS (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ FAIL ]
 Checking for non power of two support...          [ FAIL ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


output via failsafe gdm session, after running 'gnome-session' in the control terminal is identical, except that the first two checks come out "[ OK ]" and compiz works just fine.

What in the world is messing up the gdm gnome session selection?  Where can I check what gets executed when this is selected?

Note: it is messed up for all users, even pristine ones that were just created.  From failsafe, compiz works fine.

glxgears gives an error about DRI not being present.

Anyone, help?

---

