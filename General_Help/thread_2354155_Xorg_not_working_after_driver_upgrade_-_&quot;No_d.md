---
title: "Xorg not working after driver upgrade - &quot;No devices to configure&quot;"
date: 2017-02-28
forum: General Help
---

### Post by aksel-r on 2017-02-28
Hi all

I have an Intel NUC based on Braswell platform, which I am using as HTPC. In order to get proper 60fps playback of 4K HEVC (x265) content, I installed latest mesa drivers using [Padoka PPA]("https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa").

Now, I am unable to use X, due to error: "[COLOR=#000000]No devices to configure.  Configuration failed.[/COLOR]"

Please help me debug,
/var/log/Xorg.0.log: [http://paste.ubuntu.com/24084317/](http://paste.ubuntu.com/24084317/)

AFAIK, it should use i915 driver and it seems to me it attempts to do so successfully, so I do not understand where it is failing.

I am running fresh install of Ubuntu Server 16.10

Thanks in advance

---

