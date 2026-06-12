---
title: "java is Gone :("
date: 2007-02-02
forum: General Help
---

### Post by Mba7eth on 2007-02-02
Hi all , 
I have just tryied to update my 1.5 jdk to 1.6jdk from the repository. So i thought if i remove everything completly would do the work . So i typed this 
```
$sudo aptitude purge sun-java5-jdk
```
which also removed jre and java bins . I reinstall version 1.6 with the command and i wanted to check its version 
$java -version 
command not found . 

How can i get it back :( ????

---

### Post by Mba7eth on 2007-02-02
Guys I have just try to install netbeans IDE! 
It tell i have no JVM ???!!!! although i can access and see applets on the web thru firefox . 

Please any one ?

---

### Post by bollix47 on 2007-02-02
Have you tried running the following and selecting 1.6?

```
sudo  update-alternatives --config java
```

---

### Post by Mba7eth on 2007-02-02
bollix47 , Mission accomplished 
Thanks a lot :)

---

