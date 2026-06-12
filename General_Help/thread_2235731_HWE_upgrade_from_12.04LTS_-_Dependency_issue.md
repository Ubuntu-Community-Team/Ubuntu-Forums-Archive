---
title: "HWE upgrade from 12.04LTS - Dependency issue"
date: 2014-07-22
forum: General Help
---

### Post by owena1337 on 2014-07-22
Hi,

Just saw in the upgrade manager that a "New hardware support is available" so I clicked install. I was given a notice and then clicked upgrade, however following on from this I received an error which you can find [here]("http://bit.ly/1njjSdB").

I haven't touched the sources.list so I can't see there being a problem there.

Any ideas?

Thanks.

---

### Post by bapoumba on 2014-07-22
Please see here : [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264)

---

### Post by owena1337 on 2014-07-24
Fixed it by doing;

> [FONT=Ubuntu Mono]sudo apt-get install xserver-xorg-lts-precise
[/FONT]hwe-support-status --verbose 
[COLOR=#222222]sudo apt-get install linux-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty linux-image-generic-lts-trusty[/COLOR]
[COLOR=#222222][FONT=Verdana]
Thanks.
[/FONT][/COLOR]

---

### Post by bapoumba on 2014-07-24
Oh good, I'm sure it will help others :)
Please mark your thread as solved (under Thread Tools).

---

