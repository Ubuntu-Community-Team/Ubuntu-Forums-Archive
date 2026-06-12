---
title: "Cannot unlock private ssh key after installing gnome"
date: 2014-02-25
forum: General Help
---

### Post by reuben3 on 2014-02-25
I recently installed ubuntu-gnome, and kept my existing home folder (which included my .ssh folder & private keys.) Frustratingly, gnome is not letting me use these keys -- when I attempt to, from the command line, it pops up a keyring UI asking me to enter the key passphrase. I never use passphrases with keys; it's probable that I generated them without passphrases, but I can't be sure, and the gnome UI isn't taking blank.

I use these ssh keys to access various of my production servers, and this UI is essentially preventing me from doing my job. How can I turn it off, and/or get it to unconditionally accept my keys? It really is not improving security in any way; if somebody has physical access to my machine, they can just copy my .ssh folder and copy it to whatever server they like.

---

