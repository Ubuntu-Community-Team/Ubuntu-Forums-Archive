---
title: "Administrator logon without password query"
date: 2014-12-13
forum: General Help
---

### Post by kaweka on 2014-12-13
Hi, it is fresh 14.04 LTS installation.
The initial user account was downgraded by the user/admin after Ubuntu installation
to normal account without administrative privilages. "Logon without password" was then set for this account.
Additionally one account more was created, this time an Administrator account.
"Logon without password" was never set for this account.
Anyhow Ubuntu does not asks for password while the administrative account is used to log on.
What is the possible reason?

---

### Post by steeldriver on 2014-12-13
What does

```

getent group nopasswdlogin

```
say?

---

### Post by kaweka on 2014-12-13
Thanks for your question!
It lists both accounts, the normal and the administrative one.
All account managing till now was carried out using passwd command or System Control -> User Accounts (sorry it is my own translation 
from language of Ubuntu localization used here, might be not accurate).

---

### Post by steeldriver on 2014-12-13
You can remove the user(s) from the nopasswdlogin group either using usermod, or (my preference) gpasswd

```

sudo gpasswd --delete *username* nopasswdlogin

```

---

### Post by kaweka on 2014-12-13
Thanks. The password config for this administrative user must be gone broken sometimes while juggling with these two accounts.

---

