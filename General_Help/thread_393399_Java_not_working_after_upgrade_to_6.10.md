---
title: "Java not working after upgrade to 6.10"
date: 2007-03-25
forum: General Help
---

### Post by creativepragmatic on 2007-03-25
Since I upgraded to 6.10, I get the following message every time I try to run Azureus or Netbeans (both Java apps).


```
Cannot find java. Please use the --jdkhome switch.
```


Has anybody else had this problem?

I have Java 6 installed and have uninstalled and reinstalled it since upgrading.

---

### Post by smokey edgy on 2007-03-25
You may not have java in your path or you are don't have a JAVA_HOME environment variable set (or both). When you type 'set' what do you get?

---

### Post by creativepragmatic on 2007-03-25
The JAVA_HOME variable is set to the following:

```
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00/
```

---

### Post by bollix47 on 2007-03-25
If you open a terminal and type:

```
sudo update-alternatives --config java
```

does it show version 6 as being the default?

---

### Post by creativepragmatic on 2007-03-25
Yes, the asterisk is beside:

```
/usr/lib/jvm/java-6-sun/jre/bin/java
```

---

### Post by bollix47 on 2007-03-25
See if anything [_here_]("http://ubuntuforums.org/showthread.php?t=329001&highlight=jdkhome") helps.

---

### Post by creativepragmatic on 2007-03-28
Thank your for your help bollix47.  It turned out that the problem was with Netbeans and Azureus not finding Java 6.  Reinstalling both got me up and running again.

---

