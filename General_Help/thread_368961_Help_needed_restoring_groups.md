---
title: "Help needed restoring groups"
date: 2007-02-23
forum: General Help
---

### Post by qpieus on 2007-02-23
I was trying to install virtualbox and I found out I needed to be a member of the vboxusers group. I searched around here and found a reference for doing this, but I must have mis-typed the command or something because I ended up removing myself from all groups. Yes, I know, pretty dumb.

Anywho, I went in to rescue mode and added myself back to the admin group to regain the use of sudo, and have since added myself to these groups:
```
adm, cdrom, audio, video, plugdev, admin, fuse, vboxusers, floppy
```

The problem is that I think I was in way more groups than this before my little mistake though.

So far, I've verified I can do things like play music and watch videos, mount CDs or DVDs, and ssh into my file server. I just started fixing this so I'm not sure what functionality is missing, if any.

Can someone tell me what other groups I should add myself to to restore my machine to its prior condition? Maybe you could look at what groups you are a member of and let me know what's missing from my setup.

Thanks for the help!

---

### Post by po0f on 2007-02-24
qpieus,

```
[font="Courier New"]$ groups
brett adm dialout cdrom floppy audio dip video plugdev netdev lpadmin
powerdev scanner admin[/font]
```

I'm pretty sure I haven't added myself to any other groups yet.

---

### Post by qpieus on 2007-02-24
Thanks. I added myself to lpadmin (printing?)
What's netdev, dip, and powerdev?

---

### Post by Gerard Barberi on 2007-02-24
:~$ groups
gerardonlinux adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

These are the groups I'm part of.

---

### Post by qpieus on 2007-02-26
Thanks folks, I appreciate the help. My groups membership is back to normal, everything is working well.

---

