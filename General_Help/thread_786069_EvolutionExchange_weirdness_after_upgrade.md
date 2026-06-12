---
title: "Evolution/Exchange weirdness after upgrade"
date: 2008-05-07
forum: General Help
---

### Post by jkugler on 2008-05-07
After the upgrade to Hardy, I am having what seems to be network issues with the Exchange storage plugin for Evolution.

It will work sometimes, but most of the time it will hang while checking or sending mail.  An strace on the process evolution-exchange-storage shows lots of this:
```
recv(30, 0x81c1048, 5, 0)               = -1 EAGAIN (Resource temporarily unavailable)
fcntl64(30, F_GETFL)                    = 0x2 (flags O_RDWR)
recv(30, 0x81c1048, 5, 0)               = -1 EAGAIN (Resource temporarily unavailable)
fcntl64(30, F_GETFL)                    = 0x2 (flags O_RDWR)
recv(30, 0x81c1048, 5, 0)               = -1 EAGAIN (Resource temporarily unavailable)
fcntl64(30, F_GETFL)                    = 0x2 (flags O_RDWR)
recv(30, 0x81c1048, 5, 0)               = -1 EAGAIN (Resource temporarily unavailable)
fcntl64(30, F_GETFL)                    = 0x2 (flags O_RDWR)
recv(30, 0x81c1048, 5, 0)               = -1 EAGAIN (Resource temporarily unavailable)
fcntl64(30, F_GETFL)                    = 0x2 (flags O_RDWR)

```

I downgraded from 2.22 (Hardy) packages to 2.12 (Gutsy) packages, and I still have the same problem, so it would seem this to be a weird glitch in the networking in Hardy.

Has anyone seen this?  Better yet, anyone have a solution? :)

For completeness, I'm running this under KDE, but running Evolution since corporate has an Exchange server.

---

