---
title: "[ubuntu] java system.out.print freezing problem"
date: 2013-09-26
forum: General Help
---

### Post by lookit on 2013-09-26
So, I'm hoping this is posted in the correct forum. Otherwise, apologies. My problem is as follows:

I'm writing a few simple java programs (study assignments). the IDE I'm using is DrJava. Mostly, it's smooth sailing, but whenever i use System.out.print() or System.out.println(), it freezes on me. I get the feeling this is some kind of infinite loop, but the problem is not in the code (tried code I know 100% is correct, written by my professor). I've been able to narrow it down to those two commands.
Everything compiles ok, but the "prints" mess everything up. I've tried switching compilers, as DrJava seems to be giving me a choice, but to no avail; same result.  (OpenJDK 6.0-openjdk-i386 and Eclipse compiler 0.A48).

Oh, and I'm running ubuntu 12.04 on a samsung X125. The version of DrJava is drjava-20130901-r5756.

I'd be super thankful for any help. I'm not real savvy with this stuff, so in case I left out any relevant information just tell me and I'll add it.

---

### Post by v.podlednev on 2013-11-03
> **lookit said:**
> So, I'm hoping this is posted in the correct forum. Otherwise, apologies. My problem is as follows:

I'm writing a few simple java programs (study assignments). the IDE I'm using is DrJava. Mostly, it's smooth sailing, but whenever i use System.out.print() or System.out.println(), it freezes on me. I get the feeling this is some kind of infinite loop, but the problem is not in the code (tried code I know 100% is correct, written by my professor). I've been able to narrow it down to those two commands.
Everything compiles ok, but the "prints" mess everything up. I've tried switching compilers, as DrJava seems to be giving me a choice, but to no avail; same result.  (OpenJDK 6.0-openjdk-i386 and Eclipse compiler 0.A48).

Oh, and I'm running ubuntu 12.04 on a samsung X125. The version of DrJava is drjava-20130901-r5756.

I'd be super thankful for any help. I'm not real savvy with this stuff, so in case I left out any relevant information just tell me and I'll add it.

I had the same problem with Java-1.6.0-OpenJDK-amd64. Installing the Java-1.7.0-OpenJDK fix it.

---

