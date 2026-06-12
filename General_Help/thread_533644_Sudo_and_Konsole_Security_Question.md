---
title: "Sudo and Konsole: Security Question"
date: 2007-08-24
forum: General Help
---

### Post by tpg on 2007-08-24
Running Kubuntu Feisty, i have just noticed something rather odd. Konsole gives you the option to start a new root shell (Session->New Root Shell). The first time I do this, it asks for a password, as expected. However, on subsequent openings, a password is not required.

I guessed this was to do with sudo timestamps, and so closed the root konsole, and ran sudo -K as myself. After this, as expected, trying to run sudo prompts me for my password. However, even after this, a password is still not required to open the root shell from within Konsole!

Does anybody know if this is intentional, a bug, or an oversight on my part? Thanks in advance for any responses!

---

### Post by tpg on 2007-08-25
BUMP: Any ideas, anyone?

---

### Post by apetresc on 2007-08-25
kdesu (which I assume is being used to launch root terminal) has its own memory of passwords, not sudo's. You can clear it using ```
kdesu -s
```. Also if you want it to not remember the password to begin with, you can modify the shortcut to use "kdesu -n" instead of "kdesu" for launching Konsole.

This information brought to you by: kdesu --help

---

### Post by tpg on 2007-08-25
Thanks, but that doesn't solve the problem:
```
$kdesu -s
kdesu: ERROR: Daemon not running -- nothing to stop
```
tried both with and without the root session running.

EDIT: Perhaps I should make it clearer I meant a root session within a Konsole, rather than running Konsole itself as root.

---

### Post by cwaldbieser on 2007-08-26
> **tpg said:**
> Thanks, but that doesn't solve the problem:
```
$kdesu -s
kdesu: ERROR: Daemon not running -- nothing to stop
```
tried both with and without the root session running.

EDIT: Perhaps I should make it clearer I meant a root session within a Konsole, rather than running Konsole itself as root.

I get the same behavior in Dapper.  However, I noticed after some time, a assword is required again.

---

