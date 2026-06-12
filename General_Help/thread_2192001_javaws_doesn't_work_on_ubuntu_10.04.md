---
title: "javaws doesn't work on ubuntu 10.04"
date: 2013-12-05
forum: General Help
---

### Post by rdarnley on 2013-12-05
Hi,

I have a problem with javaws on Ubuntu 10.04 (I know quite ancient now!).  When I try to run my .jnlp file I get the following output in the terminal:

```
Exception in thread "main" java.lang.NullPointerException    at javax.swing.SwingUtilities.appContextGet(SwingUtilities.java:1858)
    at javax.swing.SwingUtilities.getSharedOwnerFrame(SwingUtilities.java:1828)
    at javax.swing.JWindow.<init>(JWindow.java:185)
    at javax.swing.JWindow.<init>(JWindow.java:137)
    at net.sourceforge.jnlp.runtime.JNLPSecurityManager.<init>(JNLPSecurityManager.java:121)
    at net.sourceforge.jnlp.runtime.JNLPRuntime.initialize(JNLPRuntime.java:238)
    at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:181)
    at net.sourceforge.jnlp.runtime.Boot.run(Boot.java:51)
    at java.security.AccessController.doPrivileged(Native Method)
    at net.sourceforge.jnlp.runtime.Boot.main(Boot.java:172)
```

I thought this was a problem with my .jnlp file but I get the same error message when I simply type javaws in the terminal and hit enter.

I have removed and re-installed the icedtea-netx using Ubuntu Software Centre but I see no change.

Can anyone help me?  By the way several months ago this worked fine, and now it doesn't.  Has a software update broken icedtea-netx?

Thanks in advance,

Richard

---

### Post by mörgæs on 2013-12-06
Hi, welcome to the fora.

> **rdarnley said:**
> Has a software update broken icedtea-netx?

Maybe. If so then you will not get a fix for the problem; that's exactly the reason why people should abandon old releases.

---

