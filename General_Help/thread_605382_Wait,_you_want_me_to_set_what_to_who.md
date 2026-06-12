---
title: "Wait, you want me to set what to who?"
date: 2007-11-07
forum: General Help
---

### Post by JaggedOne on 2007-11-07
```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

I just got that error message when trying to run a touchpad settings app on my laptop. How do I do that?

---

### Post by ofb on 2007-11-07
```
gksudo gedit /etc/X11/xorg.conf
```

Although before you edit a system file, make a backup. So,

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confBAK
```

And it's worth repeating what's in the beginning of that file,

> # Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

And since you're unfamiliar with this, keep your brain turned on and proceed with some caution. Like wait for a few more posts, and while waiting, try a search using that error message. This may be the first stage of a Learning Experience, rather than a quick adjustment.

---

