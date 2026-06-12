---
title: "YaCy GPG Error"
date: 2013-12-05
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-12-05
Hello,

When I attempt to upgrade YaCy, which is a decentralized search engine, I get the following error:

W: GPG error: [http://debian.yacy.net](http://debian.yacy.net) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F968B3903D886E7

I get the same problem in "Update Manager," or Synaptic Package Manager.

Please help.

Thanks Hannibal

---

### Post by bashiergui on 2013-12-05
Hmm. Normally you would decide if you trusted the software, and if so then install the key. However it looks like the developer of yacy doesn't know *how* to create a key. 
[http://bugs.yacy.net/view.php?id=79](http://bugs.yacy.net/view.php?id=79)

If you *still* want to trust yacy then you'd need to download it from yacy's site and make/install it yourself.

---

### Post by oldos2er on 2013-12-06
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F968B3903D886E7
```

---

### Post by coljohnhannibalsmith on 2013-12-06
Thank you gentlemen for your help. In the meantime I found a solution; I went into Synaptic Package Manager and individually marked YaCy for upgrade. I was never able to use Update Manager because YaCy doesn't support change logs.  I still had to go into Synaptic; but before I could upgrade everything as a group; no longer.

Thanks Hannibal

---

### Post by oldos2er on 2013-12-06
I'm not a gentleman, but you're welcome.

---

### Post by bashiergui on 2013-12-06
Good thing there were easier solutions than the one I found!

---

