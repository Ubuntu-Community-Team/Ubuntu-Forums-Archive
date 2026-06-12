---
title: "J2sdk Update 5 Install"
date: 2005-10-06
forum: General Help
---

### Post by Coriander on 2005-10-06
Hi,
I'm trying to install J2SE 5.0.
I've tried running the self extracting file directly as described here:

[http://java.sun.com/j2se/1.5.0/install-linux.html](http://java.sun.com/j2se/1.5.0/install-linux.html)

 /usr/java was created and looked fine.. but java -version was still the default:
$ java -version
SableVM version 1.1.8
- compile date and time: 2005-01-01 19:42:24 UTC
- gcc version: 3.3.5 (Debian 1:3.3.5-5)
- 'real life brokenness' features enabled
- signal based exception detection
- copying garbage collection
- bidirectional object layout
- inline-threaded interpreter



I deleted it after finding these instructions 

[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

about   creating the .deb... same thing (only /usr/java was not created.. I have no idea where Ubuntu put it..).
What am I doing wrong? Why won't it recognize the new install?
Thanks :)
Sarah

---

### Post by Hairy_Palms on 2005-10-06
hmm i think the .deb puts it in /usr/lib/j2re or something

---

### Post by Coriander on 2005-10-06
[QUOTE=Hairy_Palms]hmm i think the .deb puts it in /usr/lib/j2re or something[/QUOTE]

Yes! I set JAVA_HOME and updated PATH in ~/.bashrc

JAVA_HOME=/usr/lib/j2sdk1.5-sun
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
export PATH

And it works now.  I'm a little surprised, since none of the instructions I read mentioned needing to do this.. though I guess it's pretty logical.

Thanks!

---

