---
title: "at command storage"
date: 2017-10-23
forum: General Help
---

### Post by dik232 on 2017-10-23
Where does the [at command]("https://linux.die.net/man/1/at") store it's jobs?

In the process of migrating a server and want to take the at jobs with me

---

### Post by steeldriver on 2017-10-23
AFAIK it's 

```

/var/spool/cron/atjobs

```

From the FILES section of `man at`:

```

FILES
       /var/spool/cron/atjobs
       /var/spool/cron/atspool
       /proc/loadavg
       /var/run/utmp
       /etc/at.allow
       /etc/at.deny

```

---

### Post by dik232 on 2017-10-23
Thanks

Do you think a tar cpf and tar xpf would successfully transfer that directory?

---

