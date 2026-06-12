---
title: "Java DB core problem"
date: 2008-06-25
forum: General Help
---

### Post by Elcid247 on 2008-06-25
hi im gonna start studying java.

so i downloaded the jre, the jdk and the netbeans IDE.

neway after installing the jdk, it unpacked into 6 .rpm files.

all of them worked fine except the javadb-core.

this is the output
```

root@dhcppc5:/usr/java# rpm -iv '/usr/java/sun-javadb-core-10.3.1-4.1.i386.rpm' 
error: Failed dependencies:
	/bin/sh is needed by sun-javadb-core-10.3.1-4.1.i386
```

---

### Post by jamesstansell on 2008-06-25
First, you may not need to install Java DB separately, assuming that you want to use it.  I know the glassfish app server includes it, and I think the netbeans installer probably does too.

Second, you'll be a lot better off to not use the rpm packages.  You can install just fine either from the .bin installers or using the openjdk-6-* or sun-java6-* packages from synaptic or aptitude.

Last, I think someone posted a howto for programmers over in the programming talk forum.

---

