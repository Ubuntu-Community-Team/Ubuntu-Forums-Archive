---
title: "Tor will not load log file? causes it not to start?"
date: 2007-07-28
forum: General Help
---

### Post by C4U53 on 2007-07-28
I'm not sure why this is happening but here is the errors I'm getting

Jul 28 21:35:27.542 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Jul 28 21:35:27.544 [notice] Initialized libevent version 1.1a using method epoll. Good.
Jul 28 21:35:27.544 [warn] Fixing permissions on directory /var/lib/tor
Jul 28 21:35:27.544 [notice] connection_create_listener(): Opening Socks listener on 127.0.0.1:9050
Jul 28 21:35:27.544 [notice] connection_create_listener(): Opening Control listener on 127.0.0.1:9051
Jul 28 21:35:27.544 [warn] options_init_logs(): Couldn't open file for 'Log notice file /var/log/tor/log'
Jul 28 21:35:27.544 [notice] options_act_reversible(): Closing Socks listener on 127.0.0.1:9050
Jul 28 21:35:27.544 [notice] options_act_reversible(): Closing Control listener on 127.0.0.1:9051
Jul 28 21:35:27.544 [warn] Failed to parse/validate config: Failed to init Log options. See logs for details.
Jul 28 21:35:27.544 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

Thanks for any help!

---

### Post by C4U53 on 2007-07-28
Well I solved it..

I'm not sure which solved it maybe you can help me out

but I used "sudo nautilus" then gave root read/write .. which it didn't have? anyway.. I don't think that fixed it because I was the owner already. anyway Then I went to the log file it was directing me too just opend it up. deleted everything in it. started tor and BAM.. lol it worked.. ok.. thanks ;)

---

