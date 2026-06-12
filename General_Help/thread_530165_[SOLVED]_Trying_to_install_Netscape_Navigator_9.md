---
title: "[SOLVED] Trying to install Netscape Navigator 9"
date: 2007-08-20
forum: General Help
---

### Post by Maelgwyn on 2007-08-20
ok - so I've downloaded the latest .tar.gz from the Netscape website, and when I go into the /navigator/ folder and try to ./navigator I'm told that I'm missing a shared library. Specifically libstdc++.so.5.

I've tried to apt-get this file but it doesn't exist, and I can't find any reference to it in Synaptic.

Please help - I'd love to fiddle around with Netscape!

---

### Post by heimo on 2007-08-20
> **Maelgwyn said:**
> ok - so I've downloaded the latest .tar.gz from the Netscape website, and when I go into the /navigator/ folder and try to ./navigator I'm told that I'm missing a shared library. Specifically libstdc++.so.5.

I've tried to apt-get this file but it doesn't exist, and I can't find any reference to it in Synaptic.

Please help - I'd love to fiddle around with Netscape!

Are you running Feisty or Gutsy? Have you installed package libstdc++5 ?

---

### Post by Maelgwyn on 2007-08-20
I'm running Feisty server with fluxbox ^_^

Thanks! libstdc++5 was all I needed... I couldn't find it on Synaptic 'cause I was putting libstdc++.so.5 - what does the .so. mean?

---

