---
title: "Postfix no longer installed, but tries to load..."
date: 2007-05-01
forum: General Help
---

### Post by ben::zen on 2007-05-01
I was messing about with postfix and mutt for a while, and later gave up and uninstalled them. Now, however, every time I bring my computer out of sleep, it goes to a terminal and says, "Loading Postfix configuration." This makes no sense, and can anyone help me? BTW, I run Feisty.

---

### Post by dcstar on 2007-05-01
> **ben::zen said:**
> I was messing about with postfix and mutt for a while, and later gave up and uninstalled them. Now, however, every time I bring my computer out of sleep, it goes to a terminal and says, "Loading Postfix configuration." This makes no sense, and can anyone help me? BTW, I run Feisty.

Look in your /etc/rc* directories, of there may be an entry in the script that wakes up your PC.

You can also go into Synaptic and do a total removal of the configuration files.

---

