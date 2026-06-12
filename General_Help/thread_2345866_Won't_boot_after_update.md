---
title: "Won't boot after update"
date: 2016-12-08
forum: General Help
---

### Post by monkeybrain20122 on 2016-12-08
Hi, just has an update and Ubuntu won't boot any more the screen shows Ubuntiu logo and keep flashing. Before that everything was great. I think the culprit may be an update of xorg-video-intel this morning. This is official update. My plan is to try to update the driver again with a ppa. I can boot into recovery mode but when I choose with network I keep getting grep /etc/resolv.conf : no such file or directory. I use wifi and have no access to wired internet. Any suggestion?

Thanks

---

### Post by monkeybrain20122 on 2016-12-08
Ok I use a liveusb following instruction [here]("http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html") and update xorg-video but still have the problem, so it is something else.

---

### Post by monkeybrain20122 on 2016-12-08
The updates after which the problem occurs were 

```
Upgrade: libc6-dbg:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), libc6-dev:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), libc6:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), libc6:i386 (2.23-0ubuntu4, 2.23-0ubuntu5), locales:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), mpv:amd64 (2:0.22.0~xenial1, 2:0.22.0~xenial2), apport:amd64 (2.20.1-0ubuntu2.1, 2.20.1-0ubuntu2.2), libc-bin:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), python3-apport:amd64 (2.20.1-0ubuntu2.1, 2.20.1-0ubuntu2.2), xserver-xorg-video-intel:amd64 (2:2.99.917+git20160325-1ubuntu1.1, 2:2.99.917+git20160325-1ubuntu1.2), apport-gtk:amd64 (2.20.1-0ubuntu2.1, 2.20.1-0ubuntu2.2), libc-dev-bin:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), multiarch-support:amd64 (2.23-0ubuntu4, 2.23-0ubuntu5), python3-problem-report:amd64 (2.20.1-0ubuntu2.1, 2.20.1-0ubuntu2.2)
End-Date: 2016-12-08  13:41:32
```

Doesn't look like anything else other than xserver-xorg-video-intel might have caused the problem. I have successfully downgraded it but the problem  persists
```
Commandline: apt-get install xserver-xorg-video-intel:amd64=2:2.99.917+git20160325-1ubuntu1
Requested-By: guest-fkzm5t (999)
Downgrade: xserver-xorg-video-intel:amd64 (2:2.99.917+git20160325-1ubuntu1.2, 2:2.99.917+git20160325-1ubuntu1)
End-Date: 2016-12-08  16:26:59
```

But the problem persists. Maybe some config file was corrupted? Please help.

---

### Post by monkeybrain20122 on 2016-12-09
Any idea how to diagnose what the problem may be?

---

### Post by monkeybrain20122 on 2016-12-10
Well I reinstalledand pinned xserver-xorg-video-intel and it is working again. But the issue is not really solved. Comments are welcome and I would like to hear if anyone has the same problem.Graphic card is intel Ivybridge Why are they pushing xserver-xorg-video update for a LTS? I have not enrolled in the hes. This was really disastrous, but could be much worse if I don't have a separate /home. I forgot to clone the system this time around, crap.

---

### Post by sudodus on 2016-12-10
Many computers have had problems with the intel drivers in 16.04 (and 16.04.1) LTS. I thought the problems were solved by now, but obviously they are not. Please report your problems as a bug at Launchpad.

---

### Post by monkeybrain20122 on 2016-12-12
> **sudodus said:**
> Many computers have had problems with the intel drivers in 16.04 (and 16.04.1) LTS. I thought the problems were solved by now, but obviously they are not. Please report your problems as a bug at Launchpad.

I had no problem before updating from 2:2.99.917+git20160325-1ubuntu1.1 to 2:2.99.917+git20160325-1ubuntu1.2   I have asked for help in getting diagnostic info, but I got no reply, I couldn't wait any longer so I have reinstalled. I can't report anything now, I am not going to screw up my system again to reproduce the problem.

---

### Post by sudodus on 2016-12-12
It is too bad that you had this problem. The software for Intel graphics has changed a few times in order to fix problems with some graphics chips. Probably one of these fixed was not good for your hardware.

I'm glad it works for you now, and I can understand, that you have no strong incentive to reproduce the bug in order to report it.

---

