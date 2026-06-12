---
title: "Fail to start load kernel modules"
date: 2016-04-05
forum: General Help
---

### Post by bob68 on 2016-04-05
I have a dual boot system (windows & Ubuntu) with Ubuntu 15.10 being the default OS. On start up I see the message "FAILED TO START LOAD KERNEL MODULES"; but my system starts up & seems to run OK. Is there something I should be looking for or be concerned about?

---

### Post by v3.xx on 2016-04-05
Hi Bob

See if this will shed any light on the subject.

```
systemctl status systemd-modules-load
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

