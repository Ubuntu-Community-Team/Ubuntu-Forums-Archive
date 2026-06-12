---
title: "OpenJDK 7 without SSl 3 and with TLS 1.2"
date: 2014-07-09
forum: General Help
---

### Post by travis7 on 2014-07-09
Hello All,

          I'm currently working on setting up a java based xmpp server, and have a bit of an issue with OpenJDK. It seems out of the box with apt-get, it has ssl 3 enabled, and TLS 1.2 + TLS 2 disabled. In adition, it seems to have three weak cyphers enabled:

> [COLOR=#333333][FONT=Helvetica Neue]ECDHE-RSA-DES-CBC3-SHA
[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]EDH-RSA-DES-CBC3-SHA
[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]DES-CBC3-SHA[/FONT][/COLOR]

          Now I've been googling for a good while on this, as how to disable SSL 3 and enable TLS on OpenJDK, but seriously cannot find a result I read about the java configuration having to do with it, but have found nothing as to how to actually configure anything. I looked at how to build OpenJDK for ubuntu manually, but it seems nobody shows any flags for enabling/disabling features during the build. So that leaves me with my main question today. 

           How does one configure SSL 3 to be disabled, and TLS to be enabled in OpenJDK 7 on Ubuntu Server 14.04?

---

### Post by Gyokuro on 2014-07-09
Hi

Have you already checked the official documentation as it's mentioned what is enable/disabled: [http://docs.oracle.com/javase/7/docs/technotes/guides/security/SunProviders.html](http://docs.oracle.com/javase/7/docs/technotes/guides/security/SunProviders.html) and in your case I think there are changes in jdk8 ([https://bugs.openjdk.java.net/browse/JDK-7093640](https://bugs.openjdk.java.net/browse/JDK-7093640)).

- HTH

---

### Post by travis7 on 2014-07-09
> **Gyokuro said:**
> Hi

Have you already checked the official documentation as it's mentioned what is enable/disabled: [http://docs.oracle.com/javase/7/docs/technotes/guides/security/SunProviders.html](http://docs.oracle.com/javase/7/docs/technotes/guides/security/SunProviders.html) and in your case I think there are changes in jdk8 ([https://bugs.openjdk.java.net/browse/JDK-7093640](https://bugs.openjdk.java.net/browse/JDK-7093640)).

- HTH

Well I know JDK 7 has the capabilities for TLS 1.2, but on my system from a fresh install its disabled by default. Do you know any way of turning this on perhaps without having to change to JDK8 (which I'm not sure if its released yet)? I didnt really see anything that talked about how to manually enable/disable certain JDK/JRE features.

The section 'Protocols' under 'Enabled by default for client' is what I need to change. [CENTER][COLOR=#000000][FONT=Arial][/FONT][/COLOR][/CENTER]

---

### Post by travis7 on 2014-07-09
I just upgraded to JRE 8, and recompiled the xmpp server from source. Worked fine. :)

---

