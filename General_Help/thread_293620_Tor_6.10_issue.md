---
title: "Tor 6.10 issue?"
date: 2006-11-05
forum: General Help
---

### Post by lo_mein_dreams on 2006-11-05
When I try to start tor with: 
```
sudo /etc/init.d/tor start
```

I get this message

```
Nov 05 13:17:08.432 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Nov 05 13:17:08.434 [notice] Initialized libevent version 1.1a using method epoll. Good.
Nov 05 13:17:08.444 [warn] /var/lib/tor is not owned by this user (debian-tor, 109) but by there (1000). Perhaps you are running Tor as the wrong user?
Nov 05 13:17:08.444 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Nov 05 13:17:08.444 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
```

I don't understand what to do. This didn't happen in Breezy.


I tried running it without root access
```
/etc/init.d/tor start
```

and it just asks me this

```
Cannot access /var/run/tor directory, are you root?
```

---

### Post by bettlebrox on 2006-11-05
>/var/lib/tor is not owned by this user (debian-tor, 109) but by there (1000). 

Looks like the file or directory /var/lib/tor is *owned* by a user called *there*, and the user that tor runs as, *debian-tor*, doesn't have write access to that location. 

Have you tried chown (change ownership) of file or directory? Can you provide the output of "ls -ld /var/lib/tor"

---

### Post by lo_mein_dreams on 2006-11-05
Sweet, I changed the owner of the folder to debian-tor and it worked. It is weird that this only happened in 6.10, I've never had this problem before.

Output before change (just in case it matters at a point):

```
there@noise:~$ ls -ld /var/lib/tor
drwx------ 3 there debian-tor 176 2006-11-05 12:58 /var/lib/tor
```

Output after change:

```
there@noise:~$ ls -ld /var/lib/tor
drwx------ 3 debian-tor debian-tor 176 2006-11-05 16:46 /var/lib/tor
```

---

### Post by j-strap2 on 2006-11-05
Glad you got the problem sorted. Which version of Tor are you using currently, the standard Ubuntu package or the one from the Tor people?

---

### Post by bettlebrox on 2006-11-05
It is odd that there is a user on your system called *there*.

Can U determine when the *there* user was created?

---

