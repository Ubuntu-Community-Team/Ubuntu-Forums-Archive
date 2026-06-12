---
title: "Can't add key or ping since upgrade"
date: 2018-12-19
forum: General Help
---

### Post by person45 on 2018-12-19
I've upgrade my machine from 16.04 to 18.04 and now I can't ping or add keys

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 931FF8E79F0876134EDDBDCCA87FF9DF48BF1C90

I have web access through the browser but it's strange ping has stopped working. I've looked at a number of threads on how to get keys added, but I've not found a solution that works, each time I try and a new key I get the following erorr

Executing: /tmp/apt-key-gpghome.QLBCDGHiBz/gpg.1.sh --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 931FF8E79F0876134EDDBDCCA87FF9DF48BF1C90
gpg: keyserver receive failed: No keyserver available

Both ping and adding keys worked on 16.04. I'm going through a proxy, but the settings look to be the same as previous.

---

### Post by person45 on 2018-12-20
I've set the proxy rules in /etc/apt/apt.conf and /etc/profile.d/proxy.sh but nothing seems to work, I can still access the internet through my web browser, apt-get update works.

But when I run curl

curl google.com
curl: (35) error:1408F10B:SSL routines:ssl3_get_record:wrong version number

---

