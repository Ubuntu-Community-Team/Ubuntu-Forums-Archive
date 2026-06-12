---
title: "Touchpad error"
date: 2008-02-10
forum: General Help
---

### Post by nkobel003 on 2008-02-10
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I want to change my horizontal scroll and just view the options.  Also, there is no "SHMConfig" in xorg.

What do I do?

---

### Post by mojoman on 2008-02-10
You need to add the option SHMConfig as true in your xorg.conf.

open the file /etc/X11/xorg.conf with root privileges. To do this, open a terminal and punch in
```

sudo nano /etc/X11/xorg.conf
```

(nano is a lightweight editor, you can probably use kate, mousepad or whatever they're called but I prefer to stay in the terminal).

Now skip down to the section called called synaptics and in it add:
```
Option   "SHMConfig"   "true"
```

Press control-X, answer yes to save and exit. You need to restart X but after that gsynaptic should run (ctrl+alt+backspace to restart X)

Have a look at_[ this thread ]("http://ubuntuforums.org/showthread.php?t=373323&highlight=touchpad")_too, it has some examples from xorg.conf:

---

### Post by BenjaminGTF on 2008-02-11
I have not gone through it all the way but there is a pretty detailed HOWTO on gsynaptics here
[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

---

### Post by Michl on 2008-03-19
None of the suggestions I have seen on this forum or in the help.ubuntu...
directions work for me in Hardy and it didn't work in Gutsy either.  There
is a confirmed bug report on this issue, but it might only affect Dell
touchpads.

By the way, the various directions conflict between "on" and "true".

---

