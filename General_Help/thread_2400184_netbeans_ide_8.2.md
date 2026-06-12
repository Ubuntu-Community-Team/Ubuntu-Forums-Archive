---
title: "netbeans ide 8.2"
date: 2018-09-03
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2018-09-03
Hello, I used to have Netbeans at one point on Linux and eventually i erased it. Anyways I download ubuntu 18.04 (currently have the beta of 18.10) and I cant seem to make jdk work only jre..I downloaded the jdk java 8 and everything and its my default. I even made sure to verify the open path of java was correct. And yet when I rty to install some plugins it says I need the full JDK and not just JRE... what can I do please help.

---

### Post by sgian on 2018-09-04
Ubuntu 18.04 comes with a newer version of openjdk, which can cause a conflict when trying to downgrade to java 8.  Also when you have more than one java, you have to make the system know which is the default.  To check if any of this applies to you, post the output of 
```

java -version

```

---

### Post by idkwhatimdoing1.0 on 2018-09-04
That could be why Netbeans won't work properly... As I follow steps that I did in Ubuntu 16.04 and yes I know about the Java default version I set it to the right one.

---

