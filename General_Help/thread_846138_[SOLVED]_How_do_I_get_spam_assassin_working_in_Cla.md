---
title: "[SOLVED] How do I get spam assassin working in Claws-Mail?"
date: 2008-07-01
forum: General Help
---

### Post by spadewarrior on 2008-07-01
Hello,

I've installed the spam assassin plugin for claws-mail but spamd doesn't seem to work.

manually loading spamd shows this:```

[6849] warn: server socket setup failed, retry 1: spamd: could not create INET socket on 127.0.0.1:783: Permission denied
[6849] warn: server socket setup failed, retry 2: spamd: could not create INET socket on 127.0.0.1:783: Permission denied
[6849] error: spamd: could not create INET socket on 127.0.0.1:783: Permission denied
spamd: could not create INET socket on 127.0.0.1:783: Permission denied

```

Do I have to change something in iptables to get it to work?

Many thanks.

---

### Post by spadewarrior on 2008-07-02
Any suggestions?

---

### Post by colinleroy on 2008-07-10
> **spadewarrior said:**
> Hello,

I've installed the spam assassin plugin for claws-mail but spamd doesn't seem to work.

manually loading spamd shows this:```

[6849] warn: server socket setup failed, retry 1: spamd: could not create INET socket on 127.0.0.1:783: Permission denied
[6849] warn: server socket setup failed, retry 2: spamd: could not create INET socket on 127.0.0.1:783: Permission denied
[6849] error: spamd: could not create INET socket on 127.0.0.1:783: Permission denied
spamd: could not create INET socket on 127.0.0.1:783: Permission denied

```

Do I have to change something in iptables to get it to work?

Many thanks.

You should set ENABLED=1 instead of 0 in /etc/default/spamassassin:
sudo nano /etc/default/spamassassin

Then start the service as root, else you'll have that error you quoted:
sudo /etc/init.d/spamassassin start

Then load the plugin in Claws Mail: Configuration/Plugins.

HTH

---

