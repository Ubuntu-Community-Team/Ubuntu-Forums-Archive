---
title: "ssh password less login - not working!"
date: 2007-06-03
forum: General Help
---

### Post by {spitFire} on 2007-06-03
Hi all,
  I had setup password-less ssh entry to a couple of remote systems. Everything was working fine until yesterday. All of a sudden they stopped working. Now, every time I try ssh I'm prompted for the password. What could be wrong? The only thing I did was try aptitude upgrade! I even tried setting the whole thing again, but so far no use :(

---

### Post by statictonic on 2007-06-03
I'm assuming you were using private/public key authentication to do this?

Not sure what specifically could have gone wrong, but I'd recommend following this guide for setup.

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by fanatik on 2007-06-04
most likely permissions on some files have changed. the link should help, if not, post back.

---

### Post by cornsnap on 2007-06-04
be sure you don't have world rights on the home folder you're accessing this will prevent it from allowing you in without a password.

---

