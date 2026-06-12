---
title: "tor already start"
date: 2013-01-22
forum: General Help
---

### Post by neosk8 on 2013-01-22
Jan 22 11:58:37.416 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jan 22 11:58:37.417 [Notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
Jan 22 11:58:37.418 [Notice] Opening Socks listener on 127.0.0.1:9050
Jan 22 11:58:37.418 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jan 22 11:58:37.418 [Warning] /var/run/tor is not owned by this user (neo, 1000) but by debian-tor (116). Perhaps you are running Tor as the wrong user?
Jan 22 11:58:37.418 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Jan 22 11:58:37.418 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 22 11:58:37.418 [Error] Reading config failed--see warnings above.

I got thi message when I try to start tor.

anyone have the same problem?

I'm on ubuntu 12.04 64bit on a Dell Studio PC):P

---

### Post by omeomi on 2013-01-22
Did you use 'sudo' to start tor?

Also what is the output of 'ss -aln | grep 9050' ?

---

### Post by raja.genupula on 2013-01-22
The Op have to focus here
```
Jan 22 11:58:37.418 [Warning] /var/run/tor is not owned by this user  (neo, 1000) but by debian-tor (116). Perhaps you are running Tor as the  wrong user?
Jan 22 11:58:37.418 [Warning] Before Tor can create a control socket in  "/var/run/tor/control", the directory "/var/run/tor" needs to exist, 
```

---

### Post by neosk8 on 2013-01-22
The output with that command is null, nothing happens

I started vidalia by sudo:

Jan 22 17:15:14.103 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jan 22 17:15:14.103 [Notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
Jan 22 17:15:14.103 [Notice] Opening Socks listener on 127.0.0.1:9050
Jan 22 17:15:14.104 [Warning] Directory /var/run/tor does not exist.
Jan 22 17:15:14.104 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user and group account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Jan 22 17:15:14.104 [Warning] Directory /var/run/tor does not exist.
Jan 22 17:15:14.104 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user and group account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Jan 22 17:15:14.104 [Notice] Closing partially-constructed listener Socks listener on 127.0.0.1:9050
Jan 22 17:15:14.104 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 22 17:15:14.104 [Error] Reading config failed--see warnings above.

Could be a problem on wireless?

---

### Post by raja.genupula on 2013-01-22
do this in your terminal and try again 

```
sudo  mkdir /var/run/tor
```

---

### Post by neosk8 on 2013-01-22
after mkdir

Jan 22 18:07:30.990 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jan 22 18:07:30.990 [Notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
Jan 22 18:07:30.990 [Notice] Opening Socks listener on 127.0.0.1:9050
Jan 22 18:07:30.990 [Warning] /var/run/tor is not owned by this user (neo, 1000) but by root (0). Perhaps you are running Tor as the wrong user?
Jan 22 18:07:30.990 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Jan 22 18:07:30.990 [Notice] Closing partially-constructed listener Socks listener on 127.0.0.1:9050
Jan 22 18:07:30.990 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jan 22 18:07:30.990 [Error] Reading config failed--see warnings above.

---

