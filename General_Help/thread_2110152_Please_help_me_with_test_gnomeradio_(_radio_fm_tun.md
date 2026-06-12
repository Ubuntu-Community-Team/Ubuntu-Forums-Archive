---
title: "Please help me with test gnomeradio ( radio fm tuner) with alsa support"
date: 2013-01-29
forum: General Help
---

### Post by aaalbatrosss on 2013-01-29
Gnomeradio

Same people complain that no sound in gnomeradio because is an application based on OSS

The new systems, throwing the OSS, and there is no /dev/mixer.
I write a patch to support for looping back audio through alsa devices ( including mixer control ).
I have a request for you:
My hardware is limited to PCI tuner and can't test this feature in several types of tuners.

If you want to help me to test gnomeradio with alsa support, package build is in my ppa:
[https://launchpad.net/~geoubuntu/+archive/test](https://launchpad.net/~geoubuntu/+archive/test)

Default mixer device and channel is set to "default/Line", if for you not work change this to "hw:0/Line" or something close to your hardware.

If you tried this package would be happy with your review.
Thanks.

---

