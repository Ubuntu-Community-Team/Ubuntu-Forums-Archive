---
title: "Repository Issues"
date: 2008-01-09
forum: General Help
---

### Post by Barrett1734 on 2008-01-09
I'm having two (I assume) separate issues with the gutsy repositories. Whenever I load anything (package lists, updates etc.) I receive this error:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

The other issue is related to speed. I get speeds in the byte range whenever I try to download anything. from the repositories, yet my speed in firefox averages 600 KBs.

---

### Post by zvacet on 2008-01-09
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


In your case type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3E231AC7F4ECF181
 gpg --export --armor 3E231AC7F4ECF181 | sudo apt-key add -

---

### Post by Barrett1734 on 2008-01-09
That apparently worked to fix the authentication issue, but when I tried to reload the repo to test it took over 10 minutes. I've tried switching server locations (I'm in Ontario, Canada) and this had seemingly no effect. The current speed is 6717 B/s. It occasionally jumps to 20, but never any higher. I didn't have this issue when I first installed Gutsy, it has only been on subsequent access attempts that it happened.

After playing around with apt-get, it's fairly obvious that the key issue was unrelated to the speed issue. Authentication is fine, speed is not.

---

### Post by Barrett1734 on 2008-01-10
Any ideas?

---

