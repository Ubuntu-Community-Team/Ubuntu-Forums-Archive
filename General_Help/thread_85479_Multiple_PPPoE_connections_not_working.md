---
title: "Multiple PPPoE connections not working"
date: 2005-11-02
forum: General Help
---

### Post by stauf on 2005-11-02
I'm trying to set up my machine to be able to connect to two different ISPs via PPPoE - I've set up two entries in peers, added the username/password pairs to chap-secrets and pap-secrets and I've set up a symlink 'dsl-provider' to one of the ISPs.

I want to be able to just change the symlink to point to the other ISP's file, but when I try that, it just doesn't work. When it points to ISP_A, it connects and works perfectly, but when I disconnect, change it to point to ISP_B and reconnect, *ppp0* doesn't come up.

---

### Post by adwait on 2005-11-02
Why not just keep two files and then use
```
sudo pon <filename>
```
and
```
sudo poff
```
or, in case both are running simulatanously.
[code]sudo poff <filename>

The file need no necessarily be names dsl-provider, that's just the default name.

---

### Post by stauf on 2005-11-02
Mainly because I built a script to make life easier if I'm not around - we only ever want to be using one at a time, so I've put together a script that reconnects dsl-provider, and a script to change ISP (change the dsl-provider symlink).

---

### Post by stauf on 2005-11-05
Noone have any idea?

It's near exactly the same as if I did the pon <providera>/pon <providerb> thing mentioned above - where do I have to include all the username, passwords and other settings? I have two provider files (identical, except for the usernames), have added the password to pap-secrets and chap-secrets - do I need to add anything else?

---

