---
title: "Help Cannot install java 8 in any ubuntu version"
date: 2019-05-02
forum: General Help
---

### Post by kemoz on 2019-05-02
dears i need to install oracle java 8 for SAP
i tried to install it using the commands [/B]
&#8226;    sudo add-apt-repository ppa:webupd8team/java
&#8226;    sudo apt update
&#8226;    sudo apt install oracle-java8-installer
&#8226;    sudo apt install oracle-java8-set-default
but i have this error

```
sudo apt-get install oracle-java8-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package oracle-java8-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'oracle-java8-installer' has no installation candidate
```

i`be searched for the solution in many sites but don't find any correct solution 
any help piz
thank you

---

### Post by #&amp;thj^% on 2019-05-02
New:
> Important Oracle JDK License Update

The Oracle JDK License has changed for releases starting April 16, 2019. [https://www.oracle.com/technetwork/java/javase/terms/license/javase-license.html](https://www.oracle.com/technetwork/java/javase/terms/license/javase-license.html)

The new Oracle Technology Network License Agreement for Oracle Java SE is substantially different from prior Oracle JDK licenses. The new license permits certain uses, such as personal use and development use, at no cost -- but other uses authorized under prior Oracle JDK licenses may no longer be available. Please review the terms carefully before downloading and using this product. An FAQ is available here.

Commercial license and support is available with a low cost Java SE Subscription.

Oracle also provides the latest OpenJDK release under the open source GPL License at jdk.java.net. 
It's been said you need to setup an account first.

---

### Post by QIII on 2019-05-02
webupd8's PPA has discontinued making Java available due to licensing changes at Oracle.

While OpenJDK *should* work for most cases, if Oracle Java is required you might start [here]("https://www.oracle.com/technetwork/java/javase/downloads/index.html").

Edit:  Ninja'd!

---

