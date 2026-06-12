---
title: "[SOLVED] Java and gcc not working"
date: 2008-03-31
forum: General Help
---

### Post by ceclauson on 2008-03-31
I just recently installed Ubuntu, and have found that neither the Java runtime or the gcc seem to work.  When I tried to run a Java application, I got an exception with a long call stack that said that there's a file missing.   I then tried to use gcc to compile a C and C++ program.  One of them said that the header file was missing (stdio.h) and the other said that a file (non-header, probably binary) is missing.  What's going on here?

Thanks,
Cooper

---

### Post by ad_267 on 2008-04-01
For compiling you need to install the package build-essential.

Not sure about the java problem, where did you get the application from? If it's missing a library you can probably search for it and install in in synaptic.
Have you installed the ubuntu-restricted-extras package or the java package? This is what contains java and other things like mp3 codecs that cannot be installed automatically due to legal reasons, although I think this should change for java with it becoming open source.

---

### Post by ceclauson on 2008-06-12
I resolved the problem.

The problem with Java was that the Ubuntu installation came with the gnu Java runtime (gij), which is only a partial implementation of Java, and so won't run most applications.  To fix it, I installed Sun Java by following instructions I found online (google search "ubuntu sun java").

As for the C++ issue, I had to apt-get install some packages, and then it worked.  I had to find instructions for this online as well.

---

