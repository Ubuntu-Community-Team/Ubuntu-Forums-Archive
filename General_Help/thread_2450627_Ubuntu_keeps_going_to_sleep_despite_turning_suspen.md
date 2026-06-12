---
title: "Ubuntu keeps going to sleep despite turning suspend off"
date: 2020-09-17
forum: General Help
---

### Post by merrittjw1 on 2020-09-17
Hello all.  So I've got Ubuntu 20.04 Desktop running on a Dell R710, and I keep running into issues where eventually the server will go to sleep (at least I'm assuming it's sleep or hibernation) and the services eventually stop responding and I have to restart the server remotely or physically go to the server and move the mouse.

I've downloaded caffeine which didn't help.  I also read about "masking" the sleep, suspend, hibernate, and hybrid-sleep with the following command:

```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

This doesn't help either though.  I'm not sure why, and was hoping to get some direction on some things I could troubleshoot to fix this.  I tried looking at the dmesg and syslog to see if maybe something else was happening that is crashing the server, but wasn't able to see anything that stuck out.

Thanks in advance.

---

