---
title: "tor won't stop"
date: 2007-01-12
forum: General Help
---

### Post by Dr Small on 2007-01-12
Hello,
I have tor, on Ubuntu, and this is the commands I use to start and stop it:
```
sudo /etc/init.d/tor start
sudo /etc/init.d/tor stop
```

BTW, tor is a daemon.

So, tor wasn't working because it needed an update, so I apt-get removed it, and then apt-get installed it.
Well, I can still use the 'start' command, but when I use the stop command (as listed above), I get this error now.

```
not running (there is no /var/run/tor/tor.pid).
```
Yet, if I run the start command it says:
```
 * Starting tor daemon (tor)... Jan 12 20:05:35.642 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
                                                                         [ ok ]

```

Anyone have any suggestions?
Because I have to have a way to stop tor...

Dr Small

---

### Post by apjone on 2007-01-12
> **Dr Small said:**
> Hello,
I have tor, on Ubuntu, and this is the commands I use to start and stop it:
```
sudo /etc/init.d/tor start
sudo /etc/init.d/tor stop
```

BTW, tor is a daemon.

So, tor wasn't working because it needed an update, so I apt-get removed it, and then apt-get installed it.
Well, I can still use the 'start' command, but when I use the stop command (as listed above), I get this error now.

```
not running (there is no /var/run/tor/tor.pid).
```
Yet, if I run the start command it says:
```
 * Starting tor daemon (tor)... Jan 12 20:05:35.642 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
                                                                         [ ok ]

```

Anyone have any suggestions?
Because I have to have a way to stop tor...

Dr Small

you could kill it from the command line by finding the pid by "ps ax | grep tor"

just check if  /var/run/tor/tor.pid exists. If not try to find where the pid file is stored.

---

### Post by majoridiot on 2007-01-12
```
sudo killall tor
```

should kill it (if the proces is named tor).

---

