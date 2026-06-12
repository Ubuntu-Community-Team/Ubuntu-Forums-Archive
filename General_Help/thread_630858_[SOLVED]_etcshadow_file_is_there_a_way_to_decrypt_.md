---
title: "[SOLVED] /etc/shadow file? is there a way to decrypt the password what encryption is"
date: 2007-12-03
forum: General Help
---

### Post by teryowen on 2007-12-03
So whats the encryption thats used on these passwords? anyways to decipher them?

---

### Post by Spudgun on 2007-12-04
They're MD5 hashes. Can decrypt them with JTR, if you've got a lot of time.

---

### Post by teryowen on 2007-12-04
i dont think its md5 doesnt look like it as for decrypting MD5 these days its quite easy check this out:

[http://www.plain-text.info/](http://www.plain-text.info/)

and i found out that it just uses one way crypt function.

---

### Post by pointone on 2007-12-04
If you know Python, this should really help you out:

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/325204](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/325204)

---

