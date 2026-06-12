---
title: "How do I avoid have to keep unlocking the keyring"
date: 2018-07-28
forum: General Help
---

### Post by Odense on 2018-07-28
Lately I am getting asked to enter a password to unlock the keyring when I start my laptop. See attached screenshot.
When I have done this (usually a few times) is stops again until the next time I start the laptop.

What IS it and how do I switch it off?

---

### Post by mc4man on 2018-07-28
Are you auto logging in or booting to the greeter > login?

---

### Post by Odense on 2018-07-29
I am logging in at the greeter. The same PW works "on the keyring".

---

### Post by mc4man on 2018-08-01
shot in the dark - does this show any as installed?
```
apt-cache policy libpam-kwallet*
```

---

### Post by Odense on 2018-08-01
It doesn't look like it:

morten@morten-Lenovo-B50-10:~$ apt-cache policy libpam-kwallet*
libpam-kwallet4:
  Installed: (none)
  Candidate: 4:5.5.5-0ubuntu1.3
  Version table:
     4:5.5.5-0ubuntu1.3 500
        500 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
     4:5.5.5-0ubuntu1 500
        500 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
libpam-kwallet5:
  Installed: (none)
  Candidate: 4:5.5.5-0ubuntu1.3
  Version table:
     4:5.5.5-0ubuntu1.3 500
        500 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
     4:5.5.5-0ubuntu1 500
        500 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
morten@morten-Lenovo-B50-10:~$

What is the next thing to check?

---

### Post by Odense on 2018-08-04
No one else has any ideas?

At all?

---

