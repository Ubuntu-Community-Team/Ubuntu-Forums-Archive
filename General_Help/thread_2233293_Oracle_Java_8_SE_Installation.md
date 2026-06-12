---
title: "Oracle Java 8 SE Installation"
date: 2014-07-07
forum: General Help
---

### Post by guy-dillen on 2014-07-07
Hi,

Has Ubuntu 12.04 already an install package for installing Oracle Java 8 JDK? If not what is the recommended way to install Oracle Java 8 JDK:

[COLOR=#333333][FONT=Georgia]sudo add-apt-repository ppa:webupd8team/java[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Georgia]sudo apt-get install oracle-java8-installer

or manually installing it (extracting the zip file to e.g. /opt)?

Thanks.[/FONT][/COLOR]

---

### Post by QIII on 2014-07-07
Hello!

No, nobody, not even Microsoft, has a package to install Java.  Oracle will not allow that.

The webupd8 method is the one I have recommended as the easiest to use in the Java wiki linked in my signature.

Even Andrew (who is pretty much a one man show at webupd8.org!) does not have a "package" exactly.  webupd8 is not authorized to have the package either.  What you get is an installer that contains _*scripts*_ to automate the download and installation.

I just now added a reference to Oracle Java 8 via webupd8.org in the wiki.

---

