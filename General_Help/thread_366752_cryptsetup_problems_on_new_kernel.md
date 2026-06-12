---
title: "cryptsetup problems on new kernel"
date: 2007-02-21
forum: General Help
---

### Post by cookfromfrozen on 2007-02-21
I am using dm_crypt/cryptsetup for an encrypted home dir that mounts when I log in.  It works fine under 2.6.17-10 (the kernel Ubuntu ships with), but only partially works with vanilla 2.6.19 which I compiled.

The dm_crypt module is loaded and I can log in from a console and the encrypted image mounts (so I know dm_crypt is working under the new kernel), but I cannot log in graphically.

It appears to log in, then the screen goes black and takes me back to the login screen.

Has anyone else experienced this or how can I go about diagnosing the problem?

---

### Post by cookfromfrozen on 2007-02-21
I'm guessing it might have something to do with the libpam modules.  Anyone able to shed any more light on this?

---

### Post by cookfromfrozen on 2007-02-25
*bump* :(

---

