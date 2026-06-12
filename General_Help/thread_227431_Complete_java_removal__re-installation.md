---
title: "Complete java removal / re-installation"
date: 2006-08-01
forum: General Help
---

### Post by Culito on 2006-08-01
Hi folks,
I want to completely remove and re-install java.  I've been running Dapper for a few months now and like it, but I've always had problems with java and have probably mistakenly installed 3 or 4 versions who knows where.  How do I  completely clean up and start over?
I have a few programs that I'd like to build and I can never get the java to work - I always get an error that the java isn't in the correct path, etc. even if I change the classpath or java_path.
Can I install the latest SDK and use it for my system-wide java, and firefox plugin?
I can't seem to find any definate answers in the forums.

Thanks for lookin'.

---

### Post by siplus on 2006-08-01
I believe the default install dir for java is "/usr/java/" if you install the .bin from Sun's website.

You could just delete this directory ("rm -rf /usr/java") and run sun's binary installer.

I just installed Sun's Java SE JDK today on ubuntu. The bin file actually unpacks and runs an installshield that installs the jdk and netbeans to /opt/.

I got the JDK from [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

Hope this helps!

---

### Post by Culito on 2006-08-01
Thanks, I'll use that link to re-install.
I've deleted all the obvious directories, and used synaptic to remove all the java I had installed, but $java -version still says "java version 1.4.2"

Need to take care of that first, I guess...

---

### Post by lamadredelsapo on 2006-10-04
Once you've installed the latest JDK try this command:
```
sudo update-alternatives --config java
```

---

### Post by Ocxic on 2006-10-05
if you installed java through synaptic:
"sudo apt-get remove --purge sun-java*"

---

