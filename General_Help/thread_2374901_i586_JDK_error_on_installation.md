---
title: "i586 JDK error on installation"
date: 2017-10-20
forum: General Help
---

### Post by jayesh.patil on 2017-10-20
I got the below error 

sha256sum mismatch jdk-8u152-linux-i586.tar.gz

can you plz provide me patch for i586?

---

### Post by QIII on 2017-10-20
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2374686](https://ubuntuforums.org/showthread.php?t=2374686)

Yours appears to be a problem distinct from the original thread.

---

### Post by slickymaster on 2017-10-20
Hello jayesh.patil, welcome to the forums.

It seems that your JDK package is not downloaded correctly. Try the following```
sudo apt-get --purge remove oracle-java8-installer
sudo apt-get clean
sudo apt-get update
sudo add-apt-repository --remove ppa:webupd8team/java
sudo apt-get update
sudo apt-add-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

