---
title: "Installing Java 6.5"
date: 2008-05-06
forum: General Help
---

### Post by Huss on 2008-05-06
Hi all

I need to install java 6.5 in the next few days and can only find RPM packages on the sun site. 

If I cant install it on Ubuntu, I'll have to use Windows.

Will this do the job?
[http://www.crazysquirrel.com/computing/debian/java.jspx](http://www.crazysquirrel.com/computing/debian/java.jspx)

---

### Post by pro003 on 2008-05-06
just paste this in your terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

you'll have java installed...:KS

---

### Post by atomkarinca on 2008-05-06
If you mean java 6 then this would be enough: open up a terminal and type:

```
sudo apt-get install sun-java6-jre
```

---

### Post by jespdj on 2008-05-06
There is no "java 6.5". There's Java 5 or Java 6, but not "6.5".

You should always prefer installing software via the package management system (Synaptic or apt-get) above installing it manually (for example, by downloading it from the Sun website and installing it yourself).

---

### Post by Huss on 2008-05-06
Wow, thank you for such quick replies.

I used "sudo apt-get install sun-java6-jre" to install, which (for anyone else out there) can be done through add/remove as well. 

This will probably run what I need. I was told that I need the most recent update of version 6 - that is version 6, update 5 (6.5). I will find out if it runs tomorrow.  

Thanks again!

---

### Post by Huss on 2008-05-07
It worked!

For others, first ```
java -version 
``` to see what version of Java you are running, then:

Code: ```
apt-cache search jdk
``` to see what versions are out there. Then:
```
sudo apt-get install sun-java6-jre 
``` to install whichever version you like. Then you need to select the version with:
```
sudo update-alternatives --config java
```

---

