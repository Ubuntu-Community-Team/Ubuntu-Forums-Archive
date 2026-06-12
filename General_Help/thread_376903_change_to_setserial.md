---
title: "change to setserial?"
date: 2007-03-05
forum: General Help
---

### Post by funnyfraggle on 2007-03-05
Does anyone know if setserial has changed. I am trying to install a com port that I know is at address 0xe000, and irq11.

```

jay@ubuntu-dev:~$ sudo setserial /dev/ttyS4 port 0xe000 irq 11 autoconfig
Cannot set serial info: Invalid argument

```

```

jay@ubuntu-dev:~$ sudo setserial /dev/ttyS4 port
Missing argument for port

```

If I put anything after port I get the invalid argument error. I booted up a couple hard drives with older versions of Linux (a Suze and a Red Hat) and they worked just fine. I also couldn't find anything on the Source Forge page to indicate changes had been made.

I am using a fully patched Dapper Drake installation.

Also, if this is in the wrong forum please let me know where I should look.

-- Jay

---

