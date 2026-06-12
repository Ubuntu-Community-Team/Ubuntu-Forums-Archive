---
title: "libpulse-dev unmet dependencies in 12.04 Precise"
date: 2014-09-13
forum: General Help
---

### Post by spookybathtub on 2014-09-13
I'm running Ubuntu 12.04.5, and I want to install libpulse-dev in order to use ffmpeg.  It looks like the latest version available in the Precise repo is 1.1, which depends on libpulse0 1.1.  But I already have libpulse0 2.0 installed.  Why isn't libpulse-dev 2.0 available for Precise?  It is in the Quantal repo.

Should I try to manually install the Quantal 2.0 version?  Or downgrade libpulse0?

```
[FONT=Menlo]The following packages have unmet dependencies:[/FONT]
[FONT=Menlo] libpulse-dev : Depends: libpulse0 (= 1:1.1-0ubuntu15.4) but 1:2.0-0ubuntu1~precise2 is to be installed[/FONT]
[FONT=Menlo]                Depends: libpulse-mainloop-glib0 (= 1:1.1-0ubuntu15.4) but 1:2.0-0ubuntu1~precise2 is to be installed
[/FONT][FONT=Menlo]E: Unable to correct problems, you have held broken packages[/FONT]
```

---

### Post by ian-weisser on 2014-09-15
Downgrade.

12.04 uses mostly the same software as when it was released. Important bugfixes and security patches (including updated kernels) are included in precise-updates, but -with a few exceptions- no new releases. Software stability, not system stability, is the the 'stability' part of LTS.

Less important bugfixes and new releases are included with each new release of Ubuntu. If you want new versions, use the 6-month releases instead of LTS.

14.04, by the way, has libpulse-dev 4.0. And it probably will have 4.0 for the next five years.

---

### Post by ibjsb4 on 2014-09-15
I don't understand why this 1:2.0 package is being installed on yours and not mine.  I also run 12.04.5 and libpulse-dev installs using the 1:1.1 package.

This 1:2.0 package is not offered to me in synaptic.

[ATTACH=CONFIG]256472[/ATTACH]

---

### Post by mc4man on 2014-09-15
Maybe you had used this ppa? (and since disabled
[https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/ppa)

---

### Post by spookybathtub on 2014-09-20
I can't remember now, but it does sound likely that I used that ppa at some time in the past.  Downgrading was simple, and the problem is solved.

---

