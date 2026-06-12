---
title: "Ubuntu 12.04 unattended-upgrades package-requires installation of untrusted packages"
date: 2015-07-07
forum: General Help
---

### Post by Nick_W on 2015-07-07
Hi,

Am running Ubuntu 12.04.
One of the latest security updates is for the the "unattended-upgrades" package; specfically, an upgrade to Version 7.6+4ubuntu0.2.
The security fix is #1463663 (a fix related to UTF-8 bad format character error).

However when I try to actually do this security update with the package manager, I get "requires installation of untrusted packages - this action would require the installation of packages from unauthenticated sources". I haven't changed my package update source recently, so I am a bit puzzled. Any ideas on why I am getting this error?

My package source is the United Kingdom Ubuntu server.

Same happens with the other 2 updates I currently have - for the p7zip and x11-utils packages. I was notified of these updates at some point last week.

Thanks,
Nick

---

### Post by v3.xx on 2015-07-07
Do a manual update.  It should tell you that a key is missing and give the number.  Enter this key # and you should be good to go.
```
sudo apt-get update
```
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+error+no+pubkey&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+error+no+pubkey&sa=Search&cof=FORID:9)

---

