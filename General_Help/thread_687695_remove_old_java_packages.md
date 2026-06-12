---
title: "remove old java packages"
date: 2008-02-04
forum: General Help
---

### Post by cccc on 2008-02-04
hi

which old java packages can I remove from my gutsy without to destroy java ?
```

$ dpkg -l | grep -i java
ii  bsh                                    2.0b4-6ubuntu1                            Java scripting environment (BeanShell) Versi
ii  gij-4.1                                4.1.2-16ubuntu2                           The GNU Java bytecode interpreter
ii  gij-4.2                                4.2.1-5ubuntu5                            The GNU Java bytecode interpreter
ii  java-common                            0.26ubuntu1                               Base of all Java packages
ii  java-gcj-compat                        1.0.76-4ubuntu1                           Java runtime environment using GIJ
ii  java-package                           0.35                                      utility for building Java(TM) 2 related Debi
ii  libbcel-java                           5.2-2ubuntu2                              Analyze, create, and manipulate (binary) Jav
ii  libgcj-common                          1:4.2.1-4ubuntu2                          Java runtime library (common files)
rc  libgcj7                                4.1.0-1ubuntu8                            Java runtime library for use with gcj
ii  libgcj7-0                              4.1.2-0ubuntu5                            Java runtime library for use with gcj
ii  libgcj7-1                              4.1.2-16ubuntu2                           Java runtime library for use with gcj
ii  libgcj7-jar                            4.1.2-16ubuntu2                           Java runtime library for use with gcj (jar f
ii  libgcj8-1                              4.2.1-5ubuntu5                            Java runtime library for use with gcj
ii  libgcj8-jar                            4.2.1-5ubuntu5                            Java runtime library for use with gcj (jar f
ii  libgnucrypto-java                      2.1.0-2                                   full-featured cryptographic library in Java
ii  libhsqldb-java                         1.8.0.8-1ubuntu1                          Java SQL database engine
ii  libjaxp1.2-java                        1.2.01-2                                  Java XML parser and transformer APIs (DOM, S
ii  libjaxp1.3-java                        1.3.03-5                                  Java XML parser and transformer APIs (DOM, S
ii  libjessie-java                         1.0.1-3                                   free implementation of the Java Secure Socke
ii  libjline-java                          0.9.5-3ubuntu2                            Java library for handling console input
ii  liblog4j1.2-java                       1.2.13-4                                  Logging library for java
ii  libmx4j-java                           3.0.1-3                                   An open source implementation of the JMX(TM)
ii  libregexp-java                         1.4-4                                     regular expression library for Java
ii  libservlet2.3-java                     4.0-8ubuntu3                              Servlet 2.3 and JSP 1.2 Java classes and doc
ii  libservlet2.4-java                     5.0.30-6ubuntu1                           Servlet 2.4 and JSP 2.0 Java library.
ii  libxalan2-java                         2.7.0-4                                   XSL Transformations (XSLT) processor in Java
ii  libxerces2-java                        2.8.1-2                                   Validating XML parser for Java with DOM leve
ii  libxt-java                             0.20050823-2ubuntu4                       An implementation in Java of XSL Transformat
ii  openoffice.org-java-common             1:2.3.0-1ubuntu5.3                        OpenOffice.org office suite Java support arc
ii  sun-java6-bin                          6-03-0ubuntu2                             Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-fonts                        6-03-0ubuntu2                             Lucida TrueType fonts (from the Sun JRE)
ii  sun-java6-jdk                          6-03-0ubuntu2                             Sun Java(TM) Development Kit (JDK) 6
ii  sun-java6-jre                          6-03-0ubuntu2                             Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-plugin                       6-03-0ubuntu2                             The Java(TM) Plug-in, Java SE 6

```

---

### Post by taurus on 2008-02-04
Look at the output of this list to see how many different versions you have on your machine.  Keep the default (the one with a * in front of it) and you can remove the rest through synaptic if you wish.

```
java -version
sudo update-alternatives --config java
```

---

### Post by cccc on 2008-02-05
```

# java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
root@ania:/home/ania# update-alternatives --config java

Jest 4 alternatyw dostarczaj&#261;cych `java'.

  Wybór        Alternatywa
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.1
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java


```

---

