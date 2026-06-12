---
title: "package will not install even though missing dependency is"
date: 2013-06-27
forum: General Help
---

### Post by pksings on 2013-06-27
I'm trying to install sun-java6, the missing dependency is oracle-java7-jre,, which IS installed.  Help please. 
I have read the man page, --ignore-deps does not work, --force depends does not work, none of the posts I have found so far work. 

Any gurus out there?

Thanks in advance...

root@pooter:/home/sagetv# dpkg -i sun-java6-jre_1.7.0+update5-2~ppa1~precise_all.deb --ignore-depends=oracle-java7-jre
(Reading database ... 425212 files and directories currently installed.)
Preparing to replace sun-java6-jre 1.7.0+update5-2~ppa1~precise (using sun-java6-jre_1.7.0+update5-2~ppa1~precise_all.deb) ...
Unpacking replacement sun-java6-jre ...
dpkg: error processing --ignore-depends=oracle-java7-jre (--install):
 cannot access archive: No such file or directory
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on oracle-java7-jre; however:
  Package oracle-java7-jre is not installed.
dpkg: error processing sun-java6-jre (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 --ignore-depends=oracle-java7-jre
 sun-java6-jre



PK

---

### Post by claracc on 2013-06-28
See this link:[https://help.ubuntu.com/community/Java#Oracle_.28Sun.29_Java_6](https://help.ubuntu.com/community/Java#Oracle_.28Sun.29_Java_6), about sun java 6 it says:
> Oracle (Sun) Java 6

WARNING: Oracle Java 6 had reached its end of life in November 2012. There is at least one severe known vulnerability in this version, and since Java 6 is neither supported by Canonical nor Oracle, there may be many more! You should really not install this unless you have a specific need to do so. It is recommended that users either migrate to OpenJDK, or install Oracle Java 7.

Oracle (Sun) Java 6 is no longer available to be distributed by Ubuntu, because of license issues. 

So I would forgot about java 6 ( I would delete) and install openjdk-7-jre or oracle java 7

---

### Post by HiImTye on 2013-06-28
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
there'sbbeen several dozen high severity vulnerabilities patched in java in the last few months alone, which Java 6 hasn't received, so you should really reconsider installing Java 6

---

