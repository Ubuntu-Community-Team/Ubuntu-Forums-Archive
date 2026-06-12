---
title: "Help installing gnome launch box"
date: 2008-01-21
forum: General Help
---

### Post by barefootsanders on 2008-01-21
Hi everyone,

I'm new to installing progs on ubuntu and linux in general so I was hoping you could help me out.  I'm trying to install the keystroke launcher, gnome launch box.  I type ./configure one should and it fails with these errors:

```
checking for LB... configure: error: Package requirements (
        gtk+-2.0 >= 2.10
        gnome-vfs-2.0 >= 2.10
        libgnomeui-2.0
        libgnome-menu >= 2.10
        gnome-desktop-2.0 >= 2.10
        libebook-1.2 >= 1.8
        gconf-2.0
) were not met:

No package 'gtk+-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libgnomeui-2.0' found
No package 'libgnome-menu' found
No package 'gnome-desktop-2.0' found
No package 'libebook-1.2' found
No package 'gconf-2.0' found
```

Now I know I have all of these packages.  I've searched for them in synaptic and they are shown to be installed.  I also have build-essential installed.  I cant figure out where to go from here.  I'm running 64-bit architecture on a dual boot Dell latitude d620 with win-xp.

Any help would be much appreciated. 


Thanks,
Barefoot

---

### Post by jken146 on 2008-01-21
Are you talking about **gnome-launch-box**?  That package is in the Universe repository and can be installed through Synaptic or be typing ```
sudo aptitude install gnome-launch-box
```

---

