---
title: "gpg key trouble with automatix install"
date: 2007-03-17
forum: General Help
---

### Post by TheRingmaster on 2007-03-17
I am trying to get the gpg key for automatix and I just can't get it to stop saying this> W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems
I have imported the key many times. What is the deal?

---

### Post by Kateikyoushi on 2007-03-17
Copy paste this to the terminal, it should work.

```
gpg --keyserver subkeys.pgp.net --recv CC919A31E23C5FC3
gpg --export --armor CC919A31E23C5FC3 | sudo apt-key add -
```

---

### Post by flint_ on 2007-03-18
Thanks a lot!

This change in key should be added to the step by steps such are found at:
[http://www.howtoforge.com/automatix_ubuntu_p2](http://www.howtoforge.com/automatix_ubuntu_p2)

I am gonna try to do it on the Ubuntu forums...

Regards,

Fliunt

---

