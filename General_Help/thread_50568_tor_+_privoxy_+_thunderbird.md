---
title: "tor + privoxy + thunderbird"
date: 2005-07-20
forum: General Help
---

### Post by Fab on 2005-07-20
I installed tor and privoxy today, configured privoxy to forward socks to tor, and in firefox, gaim and x-chat it works fine.
I set privoxy as http and ssl proxy in thunderbird, as well as tor directly as socks proxy. I also tried different thunderbird proxy settings without success. I can get mail with the current one, but it's not possible to send mails...
Any advice?

Regards,
Fab

---

### Post by JonahRowley on 2005-07-20
This is covered in the Tor documentation.  Many Tor exit nodes' exit policy do not allow smtp traffic.  It would just be too easy for spammers to abuse Tor.

---

### Post by Fab on 2005-07-21
[QUOTE=JonahRowley]This is covered in the Tor documentation.  Many Tor exit nodes' exit policy do not allow smtp traffic.  It would just be too easy for spammers to abuse Tor.[/QUOTE]
 oh, i see. that would explain it ;P
thank you

---

