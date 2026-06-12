---
title: "Mini_Ubuntu"
date: 2014-10-19
forum: General Help
---

### Post by mayagrafix on 2014-10-19
Have installed Minimum Ubuntu OS on old laptop. Only program I want to use is evince PDF reader. 
Do I need to install X11? in order to get evince to run?
Will evince run from the command line? or need to use via zathura?

---

### Post by Bashing-om on 2014-10-19
mayagrafix; Hi !

Yep, evince is a GUI application and as such X is required .
see:
```

apt-cache show evince

```

And nope, one can not start evince from terminal until the x-server is started as the ap needs run in a 'display'.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-10-19
This will work
[https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation](https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation)

The startx command should open it.  If not, create a ~/.xinitrc file.
[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

---

