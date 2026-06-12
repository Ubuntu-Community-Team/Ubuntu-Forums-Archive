---
title: "Synaptic help"
date: 2007-10-20
forum: General Help
---

### Post by CM Xtasy on 2007-10-20
I cant download anything from Synaptic!  I tried using Update manager and it says

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

Since I tried installing automatix2, but that obviously failed.  I can't do anything with Update Manager or Synaptic.  Is there a solution to this?

---

### Post by ihcnet on 2007-10-20
Try doing the following:

```
wget http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -

```

---

