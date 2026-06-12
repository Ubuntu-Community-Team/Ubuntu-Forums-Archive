---
title: "i terminated Ubuntu upgrade then error when i'll continueing"
date: 2020-08-25
forum: General Help
---

### Post by bonifasius on 2020-08-25
A few hours ago i started to upgrading my Ubuntu 18.04 to 20.04
Then I realize that I'm using lxde desktop environtment, so there's many message that tell me to restart some lx service. Then I prever to stop the process, log out lx session and log in using ubuntu desktop. When i'll continue the upgrade, I can't do the upgrade with this message.

 " E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?"

Until now i'm afraid to restart this computer.
How to fix this and continueing the upgrade?


note : this is my first thread.

---

### Post by tea for one on 2020-08-25
You have more than one package operation in progress.

Is synaptic open or even another terminal using **apt**?

Also, upgrading LXDE to 20.04 may bring problems because of the change from LXDE to LXQT.

I'm pretty sure that Lubuntu users highly recommend a fresh install of Lubuntu 20.04 to avoid complications.

---

### Post by ActionParsnip on 2020-08-25
May help:
```

sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a

```

---

