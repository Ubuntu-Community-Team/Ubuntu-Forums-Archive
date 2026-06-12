---
title: "apt-get update Weirdness"
date: 2007-03-27
forum: General Help
---

### Post by quicksilver1234 on 2007-03-27
Hi All,
What's this mean? I'm using Server version.
```
apt-get update
Err http://de.archive.ubuntu.com/ubuntu dapper-security release.gpg
  Temporary failure resolving 'security.ubuntu.com'
...and it goes on for about 6 errors like that
```

---

### Post by dcstar on 2007-03-27
> **quicksilver1234 said:**
> Hi All,
What's this mean? I'm using Server version.
```
apt-get update
Err http://de.archive.ubuntu.com/ubuntu dapper-security release.gpg
  Temporary failure resolving 'security.ubuntu.com'
...and it goes on for about 6 errors like that
```

DNS and/or Network errors, try again later (or remove the ".de" from your Repositories and try again).

---

