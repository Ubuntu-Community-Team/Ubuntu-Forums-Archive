---
title: "Opera 9.5b on gutsy"
date: 2008-04-19
forum: General Help
---

### Post by Meskarune on 2008-04-19
I installed opera 9.5b...and now it will only open when I type sudo opera in the command line. How do  I change the permissions of Opera so it will work regularly?

> 
meskarune@Coconut:~$ opera
opera: Module initialization failure [8]. Generic failure (-1)
meskarune@Coconut:~$ sudo opera
[sudo] password for meskarune:
opera: $HOME set to /root. Use -personaldir if you do not want to use /root/.opera/
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


---

### Post by der_joachim on 2008-04-20
Try this. It might work. First, make sure that you have  opened a non-root console. Then issue the following command:
```

opera -pd /tmp/testopera &

```
As far as I understand, this is the 'safe mode' for opera.

---

### Post by Meskarune on 2008-04-20
Sorry that didn't help. But thanks. Opera started when I put that in...but it still won't start if I try opening with just "opera" in the command line or in the start menues.

---

