---
title: "tuned-adm - view properties?"
date: 2024-02-08
forum: General Help
---

### Post by ksl28 on 2024-02-08
Hi,

I have been looking into the tuned-adm cmdlet, to align our PostgreSQL servers running on Ubuntu 22.04.
```
tuned-adm list
``` shows an PostgreSQL profile, and i can enable it with ```
tuned-adm profile postgresql
```

But i want to see what values that are included in the postgresql tuned-adm profile, but have not found a way to do so.
Could you help clarify that?

---

### Post by Holger_Gehrke on 2024-02-08
tuned profiles are just directories in /usr/lib/tuned/. So the configuration for the postgresql profile should be in /usr/lib/tuned/postgresql/tuned.conf if it's a profile installed by the distribution or in /etc/tuned/postgresql/tuned.conf if it's a custom profile. The format of tuned.conf is documented in a manual page in section 5 ('man 5 tuned.conf' on the command line). 

Disclaimer: I'm not a user of tuned, I just have access to a search engine and had a few minutes to spare.

---

### Post by ksl28 on 2024-02-09
> **Holger_Gehrke said:**
> tuned profiles are just directories in /usr/lib/tuned/. So the configuration for the postgresql profile should be in /usr/lib/tuned/postgresql/tuned.conf if it's a profile installed by the distribution or in /etc/tuned/postgresql/tuned.conf if it's a custom profile. The format of tuned.conf is documented in a manual page in section 5 ('man 5 tuned.conf' on the command line). 

Disclaimer: I'm not a user of tuned, I just have access to a search engine and had a few minutes to spare.


That is perfect! i couldnt find that myself - so greatly appreciate your comment.

---

