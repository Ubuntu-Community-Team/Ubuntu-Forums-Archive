---
title: "enigmail problem"
date: 2005-10-14
forum: General Help
---

### Post by orawax on 2005-10-14
It seems that enigmail in thunderbird does not support 4096-bit keys, since both mine and my friends keys won't work. There's no problem with encrypting messages, the trouble is with decrypting and signing. The program   complains about a bad passphrase, but that can't be the case. Another, 2048-bit key works just fine. Is this really about 4096-bit keys, and if so, is it a general enigmail problem or just with the ubuntu build?

Here's the error message I get when trying to decrypt:

***
Error - secret key needed to decrypt message

gpg command line and output:
/usr/bin/gpg --charset utf8  --batch --no-tty --status-fd 2 -d --passphrase-fd 0 --no-use-agent 
gpg: encrypted with 2048-bit ELG-E key, ID D4ED655F, created 2004-05-19
      "<a@b.c>"
gpg: encrypted with 4096-bit ELG-E key, ID A8387317, created 2005-10-06
      "<1@2.3>"
gpg: public key decryption failed: bad passphrase
gpg: decryption failed: secret key not available
***

thanks in advance!

---

### Post by orawax on 2005-10-31
Ok, it seems that the problem was with the key (or seahorse) and not with enigmail. I created the first key with seahorse, and that didn't function with enigmail - my friend had a similar problem with a seahorse-created key. Now I use a key created with GPA, and enigmail works just fine.

---

