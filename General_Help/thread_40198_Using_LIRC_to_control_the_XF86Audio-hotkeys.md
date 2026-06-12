---
title: "Using LIRC to control the XF86Audio-hotkeys"
date: 2005-06-08
forum: General Help
---

### Post by Botsinge on 2005-06-08
I've just got LIRC to work thanks to CompEngr excellent guide at [http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc](http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc). But, I was thinking it would be very neat to map the media keys on the keyboard to the remote.

Do anyone know of a way to do this? I've tried irxevent, but even if I set "volume up" to, for example ctrl+u, sending that to whatever (root, desktop, currentwindow) doesn't work?

---

### Post by bsoric on 2005-09-22
I've just installed LIRC today, and I was wondering the exact same thing. Did you ever find out how to do it?

Brett

---

### Post by Botsinge on 2005-09-22
[QUOTE=bsoric]I've just installed LIRC today, and I was wondering the exact same thing. Did you ever find out how to do it?

Brett[/QUOTE]No, never did. I ended up using amixer to control the master volume. It works, but I  would really liked seeing that volume bar.

In case you are intrested here's the settings from my .lircrc
```
begin
    prog = irexec
    button = VOL+
    config = amixer sset Master 5+
    repeat = 2
end
begin
    prog = irexec
    button = VOL-
    config = amixer sset Master 5-
    repeat = 2
end
```

---

