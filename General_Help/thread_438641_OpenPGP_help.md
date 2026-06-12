---
title: "OpenPGP help"
date: 2007-05-09
forum: General Help
---

### Post by Indigo7 on 2007-05-09
Greetings!

I'm hopeful that someone can point me to the thread that I'm sure exists, but can't find.
My HDD failed and I'm trying to retrieve my pgp key. I think I have all of the info to do so. Would I be better off trying to revoke the old one and creating a new one?

Cheers!

---

### Post by IgnorantGuru on 2007-05-09
If you mean retrieve it off the keyserver, AFAIK the keyservers only hold the public key.  So if your secret key was lost on the HD, you'll have to create a new one.  I also don't think you can revoke the old one without the secret key.

---

### Post by euler_fan on 2007-05-09
A key has two parts, the private part and the public part. But I suspect you know the basic mechanics of the system. So, if you lose either, the whole thing fails. 

Question: can you still sign keys? If so, then your system still has the key somewhere and you should be able to use your keysigning app to get it out. If you can't still sign, then your easiest option (depending on how big your circle of trust is) would be to just go ahead and revoke the old one and get a new one.

Another question: centrally issued certificate (VeriSign, etc) or homegrown?

Good luck!

---

