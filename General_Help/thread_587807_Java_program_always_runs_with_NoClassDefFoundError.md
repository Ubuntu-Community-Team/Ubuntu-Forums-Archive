---
title: "Java program always runs with NoClassDefFoundError"
date: 2007-10-23
forum: General Help
---

### Post by walkabout2 on 2007-10-23
I have 2 programs which both give NoClassDefFoundError errors:
Exception in thread "main" java.lang.NoClassDefFoundError: org/exolab/castor/xml/ValidationException
and
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/xml/serialize/OutputFormat

In both cases, I am absolutely certain the jars that have these classes are in the CLASSPATH

Error occurs in Eclipse 3.2 and also when running using "java" from the prompt.
I take the same programs to a Windows machine, and they work fine.

System:
Ubuntu 7.04
java 6-sun
java -version = 1.6.0 (build 1.6.0-b105)

I've also done an "update-java-alternatives -s java-6-sun"

Weirdest thing is it used to work on this same platform. I was exclusively using just Eclipse 3.2 ... but then when I went to set up "java" and "javac" to use from the prompt, I got the above errors and programs also stopped working in Eclipse. I've tried to back out what I did, which I think was only:
1. edit the etc/environment file to set the CLASSPATH
2. install (via apt-get) some package that had "java" and "javac" in it ... I can't for the life of me remember what it was though. 

Does anybody have any idea what could cause this? I've been beating my head against the wall for 3 days now. Thanks.

---

