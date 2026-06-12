---
title: "Make Pam moudle return success"
date: 2016-01-20
forum: General Help
---

### Post by xp15 on 2016-01-20
I want to be able to login without 'systemd-user-sessions.service' running,
but it seems that pam wont let me do that, it says "system is booting up. see pam_nologin(8)".

I can still login in tty1 anyway, but cant pass the login screen. which file should I edit and how?

---

### Post by xp15 on 2016-01-20
I again cant login in tty1. but Ive read here: [http://man7.org/linux/man-pages/man8/systemd-user-sessions.8.html](http://man7.org/linux/man-pages/man8/systemd-user-sessions.8.html)

It says that systemd-user-sessions.service is creating the  nologin file at shutdown,  So I masked it AND stopped it before I reboot. I even  checked it before and logged out, then in. I could. Why couldn't I after the  reboot? Who created this file this time?

---

### Post by xp15 on 2016-01-20
OK I've read here: [http://linux.die.net/man/8/pam_nologin](http://linux.die.net/man/8/pam_nologin)

it says:
[B]Note,  the use of successok module argument causes the module to return  PAM_SUCCESS and as such would break such a configuration - failing  sufficient modules would lead to a successful login because the nologin  module succeeded. 

[/B]so I did ( /etc/pam.d/login ): 
```
 auth       sufficient  nologin.so
```

Still getting "system is booting up. see pam_nologin(8)" at login screen after reboot.

So I tried:
```
auth       sufficient  nologin.so  successok
```

And still. Why?

---

### Post by xp15 on 2016-01-21
OK I've finally made it.
Some of the source Ive used (they're not really related to the solution itself, but I've learned a lot) are here:
[http://askubuntu.com/questions/723219/force-pam-to-return-success](http://askubuntu.com/questions/723219/force-pam-to-return-success)

Thanks god for helping me

---

