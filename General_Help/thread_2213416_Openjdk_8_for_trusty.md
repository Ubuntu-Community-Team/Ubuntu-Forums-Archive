---
title: "Openjdk 8 for trusty?"
date: 2014-03-26
forum: General Help
---

### Post by spupazza on 2014-03-26
Is there any ppa for openjdk 8?I know there's a ppa for the closed source oracle jdk8, but I'd prefer if there was a ppa for the openjdk 8

---

### Post by jawilljr2 on 2014-03-26
[Here you go.]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")

[Here is the PPA.]("https://launchpad.net/~webupd8team/+archive/java")

I don't have Trusty installed...yet so I don't  know how well it works.

---

### Post by Gavin77 on 2014-03-26
It's been requested at [URL="https://bugs.launchpad.net/ubuntu/+source/openjdk-7/+bug/1297065"]
[needs-packaging]openjdk-8 in ubuntu[/URL]

---

### Post by eris23 on 2014-04-23
The ppa is for Oracle Java, not OpenJDK.

---

### Post by cariboo on 2014-04-23
Trusty has been released, so moved to General Help.

---

### Post by QIII on 2014-04-23
Just for a bit of back story ...

Most people do not know that one of the biggest movers and shakers in OpenJDK development in terms of resources is ... drumroll please ... Oracle.

With Oracle Java 7, Oracle declared that OpenJDK 7 would be the open source reference implementation for anything that called itself "Java" -- and that includes Oracle Java.  That is, everything "Java" must conform to the OpenJDK implementation.

Oracle Java isn't there yet, but it is moving that way.

So the distinction between the vaunted appellation "open source" for OpenJDK and "closed source" for Oracle Java has gotten a bit blurry.  This may be one of the things that the "Ravenous Monstoracle" has done right in the last few years since they bought Sun and got Java.

Given that so many Java developers have ignored OpenJDK and their code barfs when it can't find the "real" Java, it's almost hard to make a recommendation that people use OpenJDK over Oracle Java just because it is open source.  We're going to have to wait for some developers to wake up.

Don't believe it?  Try this experiment:

1.  Completely uninstall Oracle Java 7 (Oracle Java 8 is still in development.  It's not the production version.)  Make sure you uninstall the browser plugin.

2.  Install the latest version of OpenJDK 7, which I think is update 55 right now.

3.  Install the most recent version of the IcedTea browser plugin.

4.  Go the Oracle's Java test page (google "Do I have Java").

5.  Run the test.

You will be told "Congratulations!  You have the latest version of Java!"

(Cariboo907, did you mean to reopen this since you moved it?)

---

