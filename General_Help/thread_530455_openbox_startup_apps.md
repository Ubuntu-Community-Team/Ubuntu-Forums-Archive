---
title: "openbox startup apps"
date: 2007-08-20
forum: General Help
---

### Post by tronica on 2007-08-20
how do you start apps on openbox startup, i read that theres a autostart.sh in ~/.config, but there isn't one. any ideas.

---

### Post by kerry_s on 2007-08-20
you could make it or use .Xsession

```
#!/bin/sh

app 1 &
app 2 &
etc &

openbox

```

chmod +x ~/.Xsession

---

### Post by urukrama on 2007-08-20
There is a default autostart file in /etc/xdg/openbox/ Just copy that to /home/username/.config/openbox/autostart. 

See [this]("http://icculus.org/openbox/index.php/Help:Autostart") page at the openbox site. It should answer all your questions.

---

### Post by WhosRodney on 2007-08-23
tronica,

I'm having the same problem as you.  All I really want is a taskbar so my windows don't disappear when I minimize them.  Have you found the solution yet?

---

### Post by bodhi.zazen on 2007-08-23
> **WhosRodney said:**
> tronica,

I'm having the same problem as you.  All I really want is a taskbar so my windows don't disappear when I minimize them.  Have you found the solution yet?

For myself, this is the issue that keeps me with Fluxbox ; Openbox has no panel

There are a number of panels available, I like pypanel, but it does not do dual monitors :?

perlpanel is nice, although there are many to choose from ...

urukrama and kerry_s have both shown you how to configure openbox startup, are you having a problem with this ?

---

