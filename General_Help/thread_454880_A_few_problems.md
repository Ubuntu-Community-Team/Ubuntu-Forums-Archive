---
title: "A few problems"
date: 2007-05-25
forum: General Help
---

### Post by Phenax on 2007-05-25
I'm trying to set up my semi-computer-illiterate friend with Ubuntu. We've got it installed but are running into a few problems.

[1] His razer mouse needs to be replugged to recognize
[2] His fglrx drivers fail to work
```

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP

```

EDIT:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684) is the problem to fglrx drivers ...
Oh well, guess I'm poo out of luck.

---

### Post by Phenax on 2007-05-26
I solved them both.

For the razer mouse, I edited xorg.conf and changed the mouse protocol to "Auto."

For the second one, I blacklisted two kernel modules (See link to bug for the names.)

---

