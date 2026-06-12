---
title: "gpg stored paraphrase?"
date: 2017-02-13
forum: General Help
---

### Post by ronbaechle on 2017-02-13
----resolved
Logged in as different user and readded keys..now working
----

I'm trying to move some old scripts to a new box and am having an issue with a gpg decrypt script. I exported/imported the keys and secret private key.  When decrypting a file I'm getting prompted for a paraphrase.  I don't see the original script call for a paraphrase and it works.  Is it possible its stored somewhere?

Oringal script snip:
gpg --batch --no-tty -o plain.txt --decrypt Encrypted_file

---

