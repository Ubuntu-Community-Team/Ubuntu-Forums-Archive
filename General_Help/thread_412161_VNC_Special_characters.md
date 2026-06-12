---
title: "VNC Special characters"
date: 2007-04-17
forum: General Help
---

### Post by Lethargy on 2007-04-17
Hi,

I've got an install of feisty on my new mini-itx box, and for some reason VNC connections to it aren't able to produce some of the symbols, including the pipe character (|), or the less/greater than symbols (<,>).

Anyone got any suggestions?
Thanks

---

### Post by Lethargy on 2007-04-18
bump!

---

### Post by NigO on 2007-07-17
> I've got an install of feisty on my new mini-itx box, and for some reason VNC connections to it aren't able to produce some of the symbols, including the pipe character (|), or the less/greater than symbols (<,>).


Not much help, I'm afraid, but I've got the same problem.  Another desktop running 6.06 is fine, the xorg.conf Keyboard entries are the same on both.

ssh logins via PuTTY are fine, all characters in the expected places.

As an ardent command-line-user, this is extremely tiresome, I hope someone else can help.

Nigel

---

### Post by NigO on 2007-07-30
> **NigO said:**
> Not much help, I'm afraid, but I've got the same problem.  Another desktop running 6.06 is fine, the xorg.conf Keyboard entries are the same on both.

ssh logins via PuTTY are fine, all characters in the expected places.

As an ardent command-line-user, this is extremely tiresome, I hope someone else can help.

Nigel

A further observation- on the same machine, I run vino-server to share the console X session and Xvnc to permit additional sessions, the Xvnc ones work fine, the vino-server one has the above problem. whether I log in from a 6.06 vncviewer client or Windows RealVNC.  So I suspect there's a vino-server config option somewhere that is the problem...

Nigel

---

