---
title: "Public Key - SSH - Putty"
date: 2007-02-12
forum: General Help
---

### Post by ninocass on 2007-02-12
Hey all

I have managed to secure my SSH using public Key Auth however i have ran into a problem.

When i connect from a lnux box using my key it connect okay however when i try connect using putty in windows i get an error saying the key is not valid ??i have redownloaded the key from the linux box several times to ensure that its the correct key im using

```

Unable to use key file "C:\Documents and Settings\*****\My Documents\id_dsa" (OpenSSH SSH-2 private key)

```

Cheers

nino

---

### Post by ninocass on 2007-02-12
AHHH HA I found the answer!

[http://sourceforge.net/docman/display_doc.php?docid=761&group_id=1#key_conversion](http://sourceforge.net/docman/display_doc.php?docid=761&group_id=1#key_conversion)

Turns out putty and OpsnSSH use different key types.

I used the puttygen.exe to convert the key format to one that putty likes and now its working :D

You'd think there would be an aggreed standard!!!!

---

