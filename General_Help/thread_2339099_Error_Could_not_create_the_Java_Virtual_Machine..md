---
title: "Error: Could not create the Java Virtual Machine."
date: 2016-10-04
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2016-10-04
I installed openjdk-9 to use the Firefox add-on LanguageTool ([https://languagetool.org/](https://languagetool.org/)). During installation, I got the following error:

```
Setting up openjdk-9-jre-headless:i386 (9~b114-0ubuntu1) ...
Unrecognized VM option 'PermSize=128m'
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.
ignoring dump failure


```

I'm assuming that this is why the add-on is not working.

---

### Post by Tk007LwZFJW5ej on 2016-10-17
Perhaps my question wasn't clear: How do I fix the "unrecognized VM option" error? The question is not really about the add-on.

Other people have had this problem when launching applications that use Java:

[http://askubuntu.com/questions/624199/problem-with-java-while-trying-to-run-pycharm-community-4-5](http://askubuntu.com/questions/624199/problem-with-java-while-trying-to-run-pycharm-community-4-5)
[https://bz.apache.org/bugzilla/show_bug.cgi?id=58814](https://bz.apache.org/bugzilla/show_bug.cgi?id=58814)
[https://bz.apache.org/bugzilla/show_bug.cgi?id=58814](https://bz.apache.org/bugzilla/show_bug.cgi?id=58814)

but I'm getting the error on installation, so I don't know how to incorporate those solutions.

---

### Post by QIII on 2016-10-17
Hello!

Just for clarification:  Did you get that error while installing OpenJDK or when installing the add-on?  While using the add-on?

If I am not mistaken PermSize and MaxPermSize were deprecated in OpenJDK 8 and ignored by OpenJDK 9.

---

### Post by Tk007LwZFJW5ej on 2016-10-17
> **QIII said:**
> Hello!

Just for clarification:  Did you get that error while installing OpenJDK or when installing the add-on?  While using the add-on?


I'm sorry; I didn't give all the details. When I installed openjdk-9-jdk, I got the error

```
dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-9-openjdk-i386/include/linux/jawt_md.h', which is also in package openjdk-9-jdk-headless:i386 9~b114-0ubuntu1

```

I fixed that (I hope) by typing:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_i386.deb
```

And then, to complete the installation:

```
sudo apt-get -f install
```

and that's when I got the error about the unrecognized VM option.

---

