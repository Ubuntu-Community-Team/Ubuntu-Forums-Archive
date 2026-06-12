---
title: "Help fixing my own problems"
date: 2013-05-28
forum: General Help
---

### Post by gobblygoop on 2013-05-28
So I've been using Ubuntu and other distros for a couple of years and naturally I've began to tinker more and more. This sometimes leads to little quirks that usually don't amount to anything, but as a tinkerer I don't want quirks. Lately my biggest problem has been concerning shutdown. Sometimes it hangs and I have to force a shutdown. I also have began seeing a CPU process show up on my conky. It is called pxgsettings. It's never been there before. Recently I've been stopping most of my startup apps in an attempt to get RAM usage down (it idles at about 337mb now :)    While any ideas on these issues would be appreciated what I'd really like is to be pointed to info on how I can better track down my own bugs. Where can I look in my file system that shows errors and problems? Are there any great reads on bug chasing? I really want to get better at solving my own problems. I figure that's what tinkerers do. Thanks for any help.  By the way I'm running 13.04 with the 3.8.0-21 kernel.

---

### Post by mrajdl on 2013-05-29
> **gobblygoop said:**
> So I've been using Ubuntu and other distros for a couple of years and naturally I've began to tinker more and more. This sometimes leads to little quirks that usually don't amount to anything, but as a tinkerer I don't want quirks. Lately my biggest problem has been concerning shutdown. Sometimes it hangs and I have to force a shutdown. I also have began seeing a CPU process show up on my conky. It is called pxgsettings. It's never been there before. Recently I've been stopping most of my startup apps in an attempt to get RAM usage down (it idles at about 337mb now :)    While any ideas on these issues would be appreciated what I'd really like is to be pointed to info on how I can better track down my own bugs. Where can I look in my file system that shows errors and problems? Are there any great reads on bug chasing? I really want to get better at solving my own problems. I figure that's what tinkerers do. Thanks for any help.  By the way I'm running 13.04 with the 3.8.0-21 kernel.

Well I'm a tinker, tweeker, whatever you want to call it.  I have created most of my problems by doing so.  I have tried to tweak this operating system since 2008.  I have learned to just use it out of the box, don't mess with it cause it works.

---

### Post by HermanAB on 2013-05-29
"Where can I look in my file system that shows errors and problems?"
Watch the log files:
$ sudo tail -f /var/log/syslog

or
$ sudo tail -f /var/log/dmesg

and so on

---

