---
title: "LTSP + Norwegian keymap"
date: 2008-05-29
forum: General Help
---

### Post by plengnom on 2008-05-29
I've just installed hardy and got ltsp up and running. Everything works as it should, except I cannot get Norwegian keymap on the thin clients. Everything in order on the server.

I've tried setting XkbLayout = "no" both in /var/lib/tftboot/ltsp/i386/lts.conf and in /opt/ltsp/i386/etc/lts.conf (and updating image), but none of them works. Also tried every NO, "NO" etc... 

On 12 other servers it have just worked out of the box. 

Any ideas...? :confused:


edit: I can do setxkbmap no after login, and then it works.. but there has to be a way to fix this..

---

