---
title: "Dependencies problem (re)installing google-chrome"
date: 2013-06-22
forum: General Help
---

### Post by captain_rob on 2013-06-22
Hi,

I had a working Google-chrome program installed on my linux 10.4 remix but accidentaly removed it. Now I want to install this program again but get problems (using repositoryI tried the deb version also).
The command  “sudo apt-get update && sudo apt-get install -f” sorted no effect.

[I]
google-chrome-stable:
 Depends: gconf-service  but it is not installable
 Depends: libasound2 (>= 1.0.23)
 Depends: libgconf-2-4 (>=2.31.1) but it is not installable
  Depends: libgcrypt11 (>=1.4.5) but 1.4.4-5ubuntu2.1 is to be installed
 Depends: libgdk-pixbuf2.0-0 (>=2.22.0) but it is not installable
  Depends: libgtk2.0-0 (>=2.24.0) but 2.20.1-0ubuntu2.1 is to be installed
 Depends: libnspr4 (>=1.8.0.10) but it is not installable
 Depends: libnss3 (>=3.12.6) but it is not installable
  Depends: libstdc++6 (>=4.6) but 4.4.3-4ubuntu5.1 is to be installed
  Depends: libx11-6 (>=2:1.4.99.1) but 2:1.3.2-1ubuntu3.1 is to be installed[/I]

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]captain_rob; Hi !

I can imagine that the difficulties encountered are a result of version 10.04 having reached End Of Life, thus no longer supported.
Is of recommend to upgrade to a supported version.

There does exist a means to maybe limp along by converting your sources.list database to "old.releases" and perhaps be able to resolve the current issue.

Upgrade now will preclude a lot of anguish later.
[INDENT=3]
just my thought

[/INDENT]

[/COLOR]

---

