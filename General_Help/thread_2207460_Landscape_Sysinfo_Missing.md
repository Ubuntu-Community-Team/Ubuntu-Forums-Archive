---
title: "Landscape Sysinfo Missing"
date: 2014-02-23
forum: General Help
---

### Post by eyeprotocol on 2014-02-23
Hello all

I am using a famous hosting provider which provides me with dedicated root servers. A few years ago, i had ordered a server running the (new, then) 12.04 LTS 64bit version, and whenever i log in via ssh, i see something like :

  System information as of Mon Feb 24 00:09:30 UTC 2014

  System load:  0.07                Processes:           148
  Usage of /:   38.4% of 687.17GB   Users logged in:     1
  Memory usage: 12%                 IP address for eth0: 192.168.102.211
  Swap usage:   1%

At first, i did not care for this info, but i got used to taking a glance at it.

A few days ago, i ordered another 12.04 64bit dedicated root server and the greeting banner is missing. I tried if the "landscape-sysinfo" is available. It is not and a) i do not know what to install in order to make it available, b) i don't know how can i automate the appearance of that greeting banner.

Also, it got me thinking that maybe that "landscape" service was available then, but is deprecated or obsolete now?

Please assist.

---

### Post by tgalati4 on 2014-02-24
It's in the 12.10 repositories so I presume that it is still in 12.04.  Perhaps it is not installed by default?

tgalati4@Mint14-Extensa ~ $ apt-cache search landscape
landscape-client - The Landscape administration system client
landscape-client-ui - The Landscape administration system client - UI configuration
landscape-client-ui-install - The Landscape administration system client - UI installer
landscape-common - The Landscape administration system client - Common files

---

### Post by eyeprotocol on 2014-02-24
Either it is not installed by default, or my server provider has messed with the default installation scheme. Thank you for your answer. After installing those packages, will i have to take any extra steps?

---

### Post by CharlesA on 2014-02-24
No, just install the landscape-common package and it should update the motd the next time you login.

---

