---
title: "Amarok crashes X server"
date: 2008-01-21
forum: General Help
---

### Post by affected on 2008-01-21
Hi,
Recently, starting a day or two ago, whenever I try to start up Amarok, my entire X server crashes and restarts. Apart from automatic updates, most recently an update to the X.org core, I haven't changed anything of late in my configuration. Running Ubuntu 7.10. 

How could I get more info on what's actually happening? Which logs should I be looking at, or is there a way to force amarok to log it's activities into a file to see if that gets me anywhere?

Thanks.

---

### Post by affected on 2008-01-21
This is what appears at the end of the X server log (/var/log/Xorg.0.log.old )

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by Mam(O)n on 2008-01-21
I got same error:
```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]

```
X server crashes when I start mplayer with use gl/gl2 as output or when i try to start wine. But Amarok works perfectly. I think, that it has appeared after the X server has been updated through autoupdating system.

---

### Post by wayne040576 on 2008-01-22
I had the same problem with amarok tonight. I fixed it by reinstalling the NVidia driver. I find after any xorg update, the NVidia driver becomes unstable. 
I actually don't even use the version in the Ubuntu repository any more as it was giving too many problems. I just downloaded it from the NVidia site.

---

### Post by Mam(O)n on 2008-01-23
> **wayne040576 said:**
> I fixed it by reinstalling the NVidia driver.
Thanks for the hint. Updating up to the version 169.09 has solved my problem.

UPD: Also [here]("http://www.opensubscriber.com/message/debian-user@lists.debian.org/8416998.html") the reason is described and the decision of this problem is given.

---

### Post by DaveQB on 2008-01-28
Thanks guys.

I just noticed this same problem and this solved it (maybe we need to mark this thread as solved?)

Mam(O)n is right with his link.
Rather then re-installing the nvidia drivers off their site, just remove the libglx.so and link it to the libglx.so.<verison number>

```

cd /usr/lib/xorg/modules/extensions/
sudo rm -f libglx.so
sudo ln -s libglx.so.169.07  libglx.so

```

---

