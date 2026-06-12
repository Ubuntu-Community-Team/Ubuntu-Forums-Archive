---
title: "How to use PAM to restrict HTTP access for some users?"
date: 2013-02-26
forum: General Help
---

### Post by maxbb on 2013-02-26
I've read that PAM can be used to restrict HTTP access for some users, but I can't figure out how to do it in Ubuntu 12.04.

The `/etc/security/time.conf` man page contains this example:

>     All users except for root are denied access to console-login at all times:

        ```
login ; tty* & !ttyp* ; !root ; !Al0000-2400
```For this to work, `/etc/pam.d/login` needs to have a line

```
    account    requisite  pam_time.so
```This example works, and I tried to adapt it to limit HTTP access from the console. I added

  [HTML]  http ; tty* & !ttyp* ; !root ; !Al0000-2400[/HTML]to `/etc/security/time.conf`, and created `/etc/pam.d/http` with

```
    account    requisite  pam_time.so
```This doesn't work. I can still use `wget` as non-root from the console.

---

