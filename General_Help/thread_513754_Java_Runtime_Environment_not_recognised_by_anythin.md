---
title: "Java Runtime Environment not recognised by anything"
date: 2007-07-30
forum: General Help
---

### Post by Ozor Mox on 2007-07-30
I can't get any Java applications I install to recognise that I have actually installed a JRE. They usually don't do anything at all when launched from the applications menu, and when I start them from the terminal instead, they give me messages like:

```
Java version 1.5 or better is recommended in order to run FreeCol. Use --no-java-check to skip this check.

```

Even though i do have it installed. This message was given by FreeCol, and if I try the no Java check flag, it simply throws a load of exceptions and exits. Java on web pages works ok. Synaptic shows that sun-java5-bin and sun-java5-jre are both installed. I have also set this version as my default after looking at the Ubuntu community docs Java page.

Can anyone please tell me what I'm doing wrong?

---

### Post by Ozor Mox on 2007-07-31
Ok, I have made some progress. I have edited /etc/profile to include the lines:

```
#configuration for java
JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun"
export JAVA_HOME

PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
export PATH
```

and now doing java -version tells me I have Sun Java set as my JRE, and Java applications work. Is there anything else I need to do or should have done to set Java to 1.5?

---

### Post by Ozor Mox on 2007-08-01
Ok, last bump. Everywhere (most notably the wiki page on Java) says that you need to install Java from Synaptic and then run

```
sudo update-alternatives --config java
```

and select the JVM from the list to activate the required version of Java. Can anyone tell me why this does not seem to enable Java applications to work and editing /etc/profile with the $PATH stuff is necessary as well?

For future reference when I come to install Java on another two computers and can't understand why it doesn't work.

Thanks.

---

