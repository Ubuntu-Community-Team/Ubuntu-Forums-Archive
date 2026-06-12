---
title: "Should U upgrade Ubuntu 9.10 Karmic?"
date: 2014-09-09
forum: General Help
---

### Post by anthony40 on 2014-09-09
Hi,

I have an old server standing running OpenVPN, Dovecot some webmail server.  The version seems to be pretty old and I would like any thoughts on upgrading.

The server runs fine and I havn't had any issues with it. Hence, unless there are big benefits with upgrading I don't think I'll do it. Is there any security issues with running such an old version? Am I missing out on important software upgrades?

Any thoughts on this?


/Eaglecoth

---

### Post by ian-weisser on 2014-09-09
> **anthony40 said:**
> Is there any security issues with running such an old version?

Yes. You stopped receiving security updates on April 30, 2011.
You are vulnerable to every newly-published exploit in your services since then.

> **anthony40 said:**
> Am I missing out on important software upgrades?

No. I don't recall too many new features in those services.

---

### Post by anthony40 on 2014-09-09
Hi,

Ok,  seems like a good idea to upgrade then.  I should start preparing for it.  I would rather go for something with long term support. Any recommendations on what version to aim for?

Is it more  cumbersome to upgrade to later versions of the LTS?


/Anton

---

### Post by Impavidus on 2014-09-09
14.04, which is the latest version, has long term support. Server version will be supported until April 2019. I would try a clean install though, not upgrading via 10.04 and 12.04 (although both are still supported (server version at least)).

---

### Post by QIII on 2014-09-09
Hello!

I agree that upgrading piecemeal would be a recipe for a significant emotional event.

A clean install is the way to go.

---

### Post by ian-weisser on 2014-09-09
14.04 is free and supported until 2019.

Impavidus is right - a clean install will be faster than multiple upgrades, and will be less risky.
You are migrating from five-year-old versions so do expect a few hiccups.

Personally, I would setup a test environment: A VM with 14.04. Test your setup and data. Make all your mistakes there.

---

### Post by anthony40 on 2014-09-10
The idea to set up a vm and run from there sounds like a good one.  But the hardware is pretty old so I am thinking perhaps go for a completely new box and install a clean version on that one. That will achieve exactly what ian-weisser proposes but without the virtualization. I think I will go for that.  I will start a new thread in the hard ware section to discuss what hardware will best suit my needs.  Thanks for all your input guys, I was really close to going for the incremental upgrade,  thanks for bringing it to my attention that it might be painful.

---

