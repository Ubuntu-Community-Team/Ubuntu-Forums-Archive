---
title: "update the whole OS?"
date: 2008-03-15
forum: General Help
---

### Post by StOoZ on 2008-03-15
I just wondering , at the moment I have the latest 7.10.
when hardy will be released, will I have to uninstall 7.10 and install hardy or the update will take place automatically?

---

### Post by Nepherte on 2008-03-15
You will have the option to upgrade from gutsy to hardy as if it were an update.

---

### Post by Perpetual on 2008-03-15
Yes, you can do a distribution upgrade once Hardy is final (or even now if you dare!).

```

sudo apt-get update

```

then...

```

sudo update-manager -d

```

Landon.

Edit: As I said before you can upgrade now - but I would not unless you are interested in testing and prepared for breakage that *could* occur.

---

### Post by Joeb454 on 2008-03-15
You can run the Update Manager from System>Administration>Update Manager

or from a Terminal, you can simply type ```
sudo aptitude dist-upgrade
```

---

### Post by Perpetual on 2008-03-15
> **Joeb454 said:**
> You can run the Update Manager from System>Administration>Update Manager

or from a Terminal, you can simply type ```
sudo aptitude dist-upgrade
```

This is totally a question for my own knowledge and not a criticism of your instructions!  Would it be advisable if one has used apt-get rather than aptitude for the life of the installation to not switch to aptitude when doing the dist-upgrade?

With Debian I always use aptitude but with Ubuntu I always use apt-get based on things I have read.

Just wanted clarification. 

Thanks,

Landon

---

