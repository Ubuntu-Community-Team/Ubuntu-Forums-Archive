---
title: "Seahorse and importing ssh keys"
date: 2013-06-21
forum: General Help
---

### Post by nick.johnson on 2013-06-21
Hello,

Here's an odd one I found recently I was wondering if anyone can help with.

Using Ubuntu12.10, I have two SSH keys for accessing different sets of remote machines. I have my ssh config set up to use the correct key for the correct machine.
For the key which resides in .ssh/id_rsa, Seahorse pops up a dialog when I first use it asking for my passphrase.
For the key which resides in .ssh/id_rsa.work, it doesn't, I get the cli prompt.

This is normally fine, but I do have the occasional GUI that uses these keys and obviously no way for me to enter my passphrase if Seahorse doesn't give me a pop-up.

I tried importing id_rsa.work (in passwords + keys) but it doesn't have an option for me to put the imported key in ssh keys, only gnome2 or user keys.

Any else experienced this or have a way to fix it?

Cheers,
-Nick.

---

