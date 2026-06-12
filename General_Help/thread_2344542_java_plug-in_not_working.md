---
title: "java plug-in not working"
date: 2016-11-26
forum: General Help
---

### Post by engine on 2016-11-26
Firefox 50.0 on lubuntu 16.0.4

java installed:
me@myPC:~$ whereis java
java: /usr/bin/java /usr/share/java
/usr/lib/jvm/java-8-oracle/bin/java
/usr/lib/jvm/java-8-oracle/jre/bin/java
/usr/share/man/man1/java.1.gz

Java plug-in 11.111.2 for Mozilla browsers set to 'always activate'

… but the "Verify Java version" page [https://www.java.com/en/download/installed8.jsp](https://www.java.com/en/download/installed8.jsp) does not respond, a support chat system that I know needs java is not working, and webHelps using jquery for navigation do not display correctly

I'm hoping there's something simple I can do! and look forward to helpful suggestions.

---

### Post by Keith_Helms on 2016-11-27
**whereis java** is just showing you the standalone jvm.   To install the java plugin in firefox, run this command
```
sudo apt-get install icedtea-plugin
```

---

### Post by engine on 2016-11-27
Thanks! that's solved the problem with the webHelps; I'll check the chat system tomorrow.

---

### Post by engine on 2016-12-02
chat system still not working; [https://www.java.com/en/download/installed8.jsp](https://www.java.com/en/download/installed8.jsp) not working either :-{ I've (accidentally) opened a new thread with a bit more information; sorry for the confusion.

---

