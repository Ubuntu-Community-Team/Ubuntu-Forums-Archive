---
title: "Help installing jre8 over openjdk"
date: 2021-07-17
forum: General Help
---

### Post by makem2 on 2021-07-17
I need to install an Oracle version of jre8. to enable me to use:

[https://github.com/goatfungus/NMSSaveEditor](https://github.com/goatfungus/NMSSaveEditor)

I have downloaded jdk-16.0.1_linux-x64_bin.deb from:

[https://www.oracle.com/java/technologies/javase-jdk16-downloads.html](https://www.oracle.com/java/technologies/javase-jdk16-downloads.html)

```

makem@makem-pc:~$ java -version
openjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2)
OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2, mixed mode, sharing)
makem@makem-pc:~$

```

Checking: 

[URL="https://docs.datastax.com/en/jdk-install/doc/jdk-install/installOracleJdkDeb.html"]https://docs.datastax.com/en/jdk-install/doc/jdk-install/installOracleJdkDeb.html

[/URL]It does not make any mention of uninstalling the openjdk. Can anyone assist please?

---

### Post by monkeybrain20122 on 2021-07-17
You can switch between different versions of java with [update alternatives]("https://askubuntu.com/questions/740757/switch-between-multiple-java-versions").

BTW openjdk probably works and you don't need oracle java, have you tried running the app?

---

### Post by makem2 on 2021-07-17
I was told the it must be oracle as openjdk does not work for that software

---

### Post by monkeybrain20122 on 2021-07-17
> **makem2 said:**
> I was told the it must be oracle as openjdk does not work for that software


It works in openjdk

---

### Post by makem2 on 2021-07-17
> **monkeybrain20122 said:**
> You can switch between different versions of java with [update alternatives]("https://askubuntu.com/questions/740757/switch-between-multiple-java-versions").

BTW openjdk probably works and you don't need oracle java, have you tried running the app?

Yes i does work ty :)

---

