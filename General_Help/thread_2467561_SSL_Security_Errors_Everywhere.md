---
title: "SSL Security Errors Everywhere"
date: 2021-09-30
forum: General Help
---

### Post by amihart on 2021-09-30
I can't use Ubuntu because I am getting weird SSL/Handshake errors everywhere.

Navigating to certain websites, trying to git clone ANY github repository, trying to log into Minecraft, trying to install the Brave browser, this website was even giving me errors.

Anyone have any idea what could cause this? It only does it in Ubuntu, specifically I'm using 20.04.

1.

[IMG]https://i.imgur.com/pjdcr03.png[/IMG]

2.

[IMG]https://i.stack.imgur.com/Z0XH4.png[/IMG]

3.

[IMG]https://i.stack.imgur.com/JVQaE.png[/IMG]

4.

 [IMG]https://i.stack.imgur.com/vRu3g.png[/IMG]

---

### Post by amihart on 2021-09-30
Ironically, this website was giving me SSL errors but suddenly just started working for some reason.

---

### Post by amihart on 2021-09-30
Well I gave up trying to fix it so I installed 21.04 instead and it seems to be working? I guess moral of the story is 20.04 is buggy and don't use it.

---

### Post by CharlesA on 2021-09-30
> **amihart said:**
> Well I gave up trying to fix it so I installed 21.04 instead and it seems to be working? I guess moral of the story is 20.04 is buggy and don't use it.\

Ubuntu 20.04 is the Long Term Support (LTS) release and is supported until 2025, where Ubuntu 21.04 is a regular release and supported for 9 months (Until Jan 2022).

The error you were getting is unlikely to do with Ubuntu itself.

With that said - this site and many others use certificates from Let's Encrypt.

Your SSL errors may have been related to this as that particular certificate expired on 09/30/2021.
[https://letsencrypt.org/docs/dst-root-ca-x3-expiration-september-2021/](https://letsencrypt.org/docs/dst-root-ca-x3-expiration-september-2021/)

I don't know if that was the cause of your issue since you didn't post any details about the certificates you were having issues with, but that's likely why it started working at random.

---

### Post by DuckHook on 2021-09-30
> **amihart said:**
> Well I gave up trying to fix it so I installed 21.04 instead and it seems to be working? I guess moral of the story is 20.04 is buggy and don't use it.
In fact, 20.04 is *less* "buggy" than 21.04. This is true of all LTS releases in general. 20.04 is an LTS release and has had a year and a half to iron out most of its bugs.

You probably had a corrupted certificate database. It's not uncommon, and can happen to any release of any OS, FOSS or commercial. If you are happy with 21.04, I would suggest that you stay with it. The next LTS, 22.04, is coming out in seven months, at which time you may wish to get off the upgrade hamster wheel and get back to running LTS versions. Until then, if 21.04 works, then go with it.

---

### Post by amihart on 2021-10-01
My install was fresh and I tried it on multiple 20.04 flavors and the issue was repeated. The fact this occurs on multiple 20.04 flavors and not on 21.04 nor on Windows is absolute proof this is an issue in the software for 20.04, maybe the issue is not specific to the OS itself but to the software that written for  it is not up to date. I didn't post any certificate details because I don't know anything about how SSL works to identify what certificates in the software is causing the problem to update those. The closest thing to a solution I found was someone mentioned recompiling git with a different library fixes the bug and it seemed to, but I could not figure out how to fix the bug with the other software. If this is an issue that is just bugged in all specific pieces of the software and not a general issue then I'll have to open a bug report for all these individual pieces of software on their respective sites and so here is probably not the best place to ask about it, but I thought it might be a general issue since it affects so many programs but it looks now like it might not be a general issue.

---

