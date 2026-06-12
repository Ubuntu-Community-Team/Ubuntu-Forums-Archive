---
title: "Choosing DE with startx"
date: 2013-02-05
forum: General Help
---

### Post by Gster4 on 2013-02-05
I know how to change /etc/default/grub to boot to text. but when I use startx, I get no unity, no compiz, if I use "startx /usr/bin/fluxbox" i get the fluxbox DE.  i have Gnome3, KDE and Unity installed also, how to i use them with startx

---

### Post by Cheesemill on 2013-02-05
You need to edit your ~/.xinitrc file. There should be an exec line that specifies which DE to start. Mine looks like this for cinnamon...
```
#!/bin/sh
#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)

if [ -d /etc/X11/xinit/xinitrc.d ]; then
  for f in /etc/X11/xinit/xinitrc.d/*; do
    [ -x "$f" ] && . "$f"
  done
  unset f
fi

# exec gnome-session
# exec startkde
# exec startxfce4
# ...or the Window Manager of your choice
exec gnome-session-cinnamon

```

I'm not exactly sure what the correct exec option is for a Unity session but you should be able to Google for it.

---

### Post by Gster4 on 2013-02-05
found out I didn't have an .xinitrc file.  modified to start kde and it works, I think "unity" starts unity, but I haven't tried it

---

