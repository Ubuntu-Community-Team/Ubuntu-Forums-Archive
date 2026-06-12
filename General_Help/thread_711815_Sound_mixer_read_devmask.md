---
title: "Sound_mixer_read_devmask"
date: 2008-03-01
forum: General Help
---

### Post by Gokee2 on 2008-03-01
Hello all,
I am having the bug [https://bugs.launchpad.net/ubuntu/+source/aumix/+bug/145805](https://bugs.launchpad.net/ubuntu/+source/aumix/+bug/145805) on a new install of xubuntu 7.1 on a laptop. I ran apt-get update and apt-get install aumix and apt-get dist-upgrade but am still getting SOUND_MIXER_READ_DEVMASK if I try and start aumix.  Any idea why this would be and how to fix it?
Thanks

---

### Post by Gokee2 on 2008-03-02
Well, I guess no one is around to help.  I ended up downloading the hardy package of aumix and installing with dpkg -i.  It seems to work, but its not really what I had in mind.

---

### Post by TheIdiot on 2008-03-02
The latest gutsy aumix package is broken. The method you decided to use was one way. Another is to repackage the same version from [http://packages.ubuntu.com](http://packages.ubuntu.com). Another way is to enable gutsy-proposed in your sources.list, run apt-get update, install aumix that way, then disable gutsy-proposed again

---

### Post by Gokee2 on 2008-03-04
> **TheIdiot said:**
> The latest gutsy aumix package is broken. The method you decided to use was one way. Another is to repackage the same version from [http://packages.ubuntu.com](http://packages.ubuntu.com). Another way is to enable gutsy-proposed in your sources.list, run apt-get update, install aumix that way, then disable gutsy-proposed again

Where do I find proposed?  Can I download one proposed package from a website somewhere if I need to?

Thanks

---

