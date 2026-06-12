---
title: "No_Pubkey causing problems with apt-get update"
date: 2007-09-17
forum: General Help
---

### Post by Cobbs on 2007-09-17
Hey,

I have been looking through the other posts trying to fix my problem but nothing has fixed it.  When I run a "sudo apt-get update" the output is as such:

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I am running feisty, I just can't figure out how to get the key (I've only been using linux for about 2 months)

Thanks!

---

### Post by FuturePilot on 2007-09-17
Run this command in a terminal, The error  should disappear afterwards
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Cobbs on 2007-09-17
Thanks FuturePilot, that fixed it :)

---

### Post by FuturePilot on 2007-09-17
No problem:)

---

### Post by bodhi.zazen on 2007-09-17
FYI, you can ignore those erroers if you wish. You will get those warnings, but you will still be able to install from the reops.

The public key is used to increase security, so you know you are in fact downloading from the source you think you are.

---

### Post by Cobbs on 2007-09-17
I didn't know that about the pub keys, thanks for that tip!

---

