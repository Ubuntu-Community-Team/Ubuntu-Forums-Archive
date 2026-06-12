---
title: "Superuser configuration errors"
date: 2006-07-04
forum: General Help
---

### Post by TMC on 2006-07-04
I've just had reason to go into su  mode in the terminal and, on
entering the password, got the following configuration errors

configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)

This has only happened since upgrading from Breezy to Dapper.

Could someone shed some light on these, please - and let me know if I
should be concerned?

Many thanks in advance,

David Shaw

---

### Post by Ramses de Norre on 2006-07-04
```
sudo mv /etc/login.defs /etc/login.defs.bak
sudo cp /etc/login.defs.dpkg-dist /etc/login.defs
```

---

### Post by TMC on 2006-07-04
That did the trick, many thanks!  :D 

David Shaw

---

