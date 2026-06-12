---
title: "X11 slow over ssh"
date: 2008-02-28
forum: General Help
---

### Post by who_cares on 2008-02-28
Okay, I'm trying to forward pidgin and maybe firefox over ssh, the problem is all the remote windows freeze up a lot. I know I shouldn't expect the same performance that I would get if I were using them locally, but is there any settings I can change to help speed things up a little? Right now I can't even get the add account window in pidgin to fully appear.

---

### Post by bodhi.zazen on 2008-02-28
Try the -vv flag to see if there is a connection problem.

```
ssh -vvX user@server
```

Could also be a time out ? Try adding keep alive.

Last, try using compression.

```
ssh -XC -c blowfish user@server
```

---

