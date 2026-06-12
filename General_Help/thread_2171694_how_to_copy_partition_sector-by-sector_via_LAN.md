---
title: "how to copy partition sector-by-sector via LAN?"
date: 2013-09-01
forum: General Help
---

### Post by tmp72 on 2013-09-01
How i can copy partition sector-by-sector under ubuntu (liveUSB persistencelubuntu 13.04) via LAN network?

I have to backup partition from bad block hdd using LAN (i'm not able connect additional hdd to this laptop).

---

### Post by sudodus on 2013-09-01
It is possible using ***Clonezilla*** via the LAN. But I don't know what happens at a bad block, it might stop with an error message.

*Edit*: Maybe you should use ***ddrescue*** for that purpose, and if necessary move your bad disk to another computer. The info pages of ddrescue are good, so read 

```
info ddrescue
```

[COLOR=#696969]With ***Clonezilla*** you can use an SSH server or an SAMBA or NTS server. I think it is easiest to set up an SSH server in a linux system. See this link for a starter

[/COLOR][URL="http://clonezilla.org/general-live-use.php"][COLOR=#696969]http://clonezilla.org/general-live-use.php[/COLOR]
[/URL]

---

