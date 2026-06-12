---
title: "Open Office Base - Java"
date: 2006-11-11
forum: General Help
---

### Post by ColinG on 2006-11-11
Please, please can somebody help. I've trawled these forumas and Google but due, probably to my ineptitude, I have been unable to fimd an answer.

I have Open Office running ion Ubuntu Edgy but I cannot get the database element to perform. I try to create a database and all goes well until I get to creating a form. I click on the wizard and nothing happens. This may be a java thinmg I believe but I have Suns Java 1.5 installed. My jvm.config follows.


# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr

---

### Post by taurus on 2006-11-11
Open a terminal and at the prompt, paste the output of this command here.

```
java -version
```

---

### Post by ColinG on 2006-11-11
[
ColinQUOTE=taurus;1744583]Open a terminal and at the prompt, paste the output of this command here.

```
java -version
```[/QUOTE]

countryman@countryman-desktop:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)


See above and thanks for helping:) 
Colin

---

### Post by ColinG on 2006-11-13
Can nobody help? Are we saying OO Base is a no go?

Thanks

---

### Post by geokok1981 on 2006-11-17
I have the same problem.
OO base is a no go at least in edgy. Maybe other distros have no problems.

---

### Post by ColinG on 2006-11-17
It is certainly K/Ubuntu specific in my opinion. I am currently trying FC6 and it was the same but after some updates it has cleared on both the 32 bit and 64 bit varients. As I need a decent(ish) database I will have to adopt FC6 - it is not a bad distro anyway.

---

### Post by giuliastro on 2006-11-25
Same problem here with Edgy. I found wizards work if you use "free software foundation JRE 1.4.2". Don't ask me what it is and why Sun JRE doesn't work though...

---

### Post by mark2741 on 2006-11-25
Works fine in Edgy with gnome. Then again, I'm using JDK 1.5 instead of the JRE. Perhaps that could be the difference?

---

