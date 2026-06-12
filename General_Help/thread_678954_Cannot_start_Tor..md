---
title: "Cannot start Tor."
date: 2008-01-26
forum: General Help
---

### Post by SonicChao on 2008-01-26
```
Setting up tor (0.1.0.16-1ubuntu2.1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
 * Starting tor daemon (tor)...                                                                                                                                                    Jan 26 13:44:04.526 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jan 26 13:44:04.527 [warn] /var/lib/tor is not owned by this UID (118). You must fix this to proceed.
Jan 26 13:44:04.528 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jan 26 13:44:04.528 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
                                                                                                                                                                            [fail]
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried:
```
sudo chown nogroup:tor /var/lib/tor
```
and it said invalid user. :|

---

### Post by taurus on 2008-01-26
You need to look in /etc/group to see which one has an id of 118.  On my Gutsy, gdm has an ID of 118.

```
cat /etc/group
```

---

### Post by SonicChao on 2008-01-26
> **taurus said:**
> You need to look in /etc/group to see which one has an id of 118.  On my Gutsy, gdm has an ID of 118.

```
cat /etc/group
```

```
debian-tor:x:118:
```
How would I set /var/lib/tor to that?

---

### Post by taurus on 2008-01-26
Try something like

```
sudo chown -R debian-tor:debian-tor /var/lib/tor
```

---

### Post by SonicChao on 2008-01-26
> **taurus said:**
> Try something like

```
sudo chown -R debian-tor:debian-tor /var/lib/tor
```

```
Jan 26 14:25:15.256 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jan 26 14:25:15.260 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Jan 26 14:25:15.260 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jan 26 14:25:15.261 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
```

:|

EDIT: Alright, I understand why that happened, it's because I wasn't root. When I typed 'sudo /etc/init.d/tor start':

```
 * Starting tor daemon (tor)...                                                 
Jan 26 14:27:04.583 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
                                                                         [ ok ]
```

However, when I use Tor button to say "Tor Enabled", Firefox claims that the proxy it is configured to use is refusing connectins.

---

### Post by taurus on 2008-01-26
Now /var/log/tor wants you, 1000, to be the owner.

```
sudo chown -R 1000 /var/log/tor
```

---

### Post by SonicChao on 2008-01-26
> **taurus said:**
> Now /var/log/tor wants you, 1000, to be the owner.

```
sudo chown -R 1000 /var/log/tor
```

It's still saying the proxy server is refusing connections.

---

### Post by SonicChao on 2008-01-26
Alright, this is in the log.

```
Jan 26 14:31:08.280 [notice] Application request when we're believed to be offline. Optimistically trying again.
Jan 26 14:31:10.196 [warn] You are running Tor version 0.1.0.16, which will not work with this network.
Please use one of 0.1.2.17,0.1.2.18,0.1.2.19,0.2.0.6-alpha,0.2.0.7-alpha,0.2.0.8-alpha,0.2.0.9-alpha,0.2.0.10-alpha,0.2.0.11-alpha,0.2.0.12-alpha,0.2.0.13-alpha,0.2.0.14-alpha,0.2.0.15-alpha,0.2.0.16-alpha,0.2.0.17-alpha.
Jan 26 14:31:10.239 [notice] No Tor server exists that allows exit to [scrubbed]:6667. Rejecting.
```

---

