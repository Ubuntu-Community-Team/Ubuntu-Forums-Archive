---
title: "ATI/Beryl help"
date: 2006-12-27
forum: General Help
---

### Post by vaskark on 2006-12-27
I'm using the instructions found here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)  with a few changes ...

1) the repo I'm using is deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) edgy main-edgy
2) In gnome sessions I'm starting 'beryl-manager' not 'beryl.

'fglrxinfo' gives:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

So I log in and see the wavy beryl splash screen and I think I've done it. Then I try to move a window and it's frozen. Then I get booted back to the gdm log in screen.

Can anyone help me with this? I've been trying for ages to get this stuff working and it's turning my brain to mud.

Thanks.

---

### Post by dbbolton on 2006-12-27
why aren't you running beryl at startup ?

do you have a backup manager selected ?

---

### Post by vaskark on 2006-12-27
> **dbbolton said:**
> why aren't you running beryl at startup ?
do you have a backup manager selected ?
Well, I first tried running 'beryl' but when I logged in I had no window decorations at all. I checked and found that beryl wasn't running so I started it from the CLI and got this message:

XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

I found the tip of using 'beryl-manager' from another thread.

In my notification tray there's a beryl icon and right-clicking on it shows that metacity is my backup window manager.

---

### Post by ~LoKe on 2006-12-27
For the window decorations, you might need this in your xorg file.
> Option "AddARGBGLXVisuals"      "True"

---

### Post by vaskark on 2006-12-27
> **~LoKe said:**
> For the window decorations, you might need this in your xorg file.
So if I do add this, should I go back to starting 'beryl' or should I stick with 'beryl-manager'? And where exactly do I add this in xorg.conf? In the Device section?

---

### Post by ~LoKe on 2006-12-27
I would suggest beryl-manager.

---

### Post by vaskark on 2006-12-27
K I added that line, and was able to log in ok and see all the effects. But it still crashes any time I try to move a window.
](*,)
Is there a log file I can look at to see what the error being generated is so I can post it here? Or, is there a certain effect pertaining to window movement that I could disable?

---

### Post by vaskark on 2006-12-28
*bump*

:cry:

---

### Post by beerorkid on 2006-12-28
might want to try SVN
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

that is what I use.  just see if a update/dist-upgrade will fix your problems

I would also suggest following the [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) beryl wiki if you still have problems.

---

### Post by vaskark on 2006-12-29
> **beerorkid said:**
> might want to try SVN
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

that is what I use.  just see if a update/dist-upgrade will fix your problems

I would also suggest following the [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu) beryl wiki if you still have problems.
I activated the beryl-svn repo, and I do notice that the effects are a lot faster & smoother for me. But it still crashes whenever I try to move a window. I followed everything in that wiki to set this all up (the edgy ubuntu guide was my original source, but it seems the exact same).

---

