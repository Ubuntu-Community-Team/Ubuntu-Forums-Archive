---
title: "Play movies using SSH"
date: 2008-06-03
forum: General Help
---

### Post by relix on 2008-06-03
I've connected a PC to my TV, and network. Now I would like to start a mediaplayer from my other PC.

Synergy doesn't work because I can't log in to gdm yet.

VNC doesnt' work because of the same reason, I believe.

Is there something else I can use to start a mediaplayer using ssh? (Or another protocol)

---

### Post by spydon on 2008-06-03
You can use
```
ssh -X username@server
```
and load movies from the server.
Like
```
vlc movie.ogg
```

You also need to add or change a line in /etc/ssh/sshd_config
```
X11Forwarding yes
```

---

### Post by relix on 2008-06-03
Ah, yes, but it's the other way around that I want it to work :).

PC A: Connected to TV, network, but no keyboard or mouse
PC B: Connected to network, keyboard, mouse

I want to use PC B to log in to PC A and start a movie on PC A, so that it is shown on the TV.

I'm currently using auto-login and then synergy, but it's kind of a security risk...

---

### Post by GammaPoint on 2008-06-03
I forget if this is the right syntax, but maybe you can say 

> DISPLAY="0.0" mplayer *movie*

after you ssh onto the machine with the TV. If the TV is display #1 then perhaps you would say

> DISPLAY="0.1" mplayer *movie*

but I don't know. Never tried it.

---

