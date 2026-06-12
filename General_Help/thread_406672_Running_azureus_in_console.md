---
title: "Running azureus in console"
date: 2007-04-11
forum: General Help
---

### Post by rpr on 2007-04-11
Hi,

I am trying to run azureus in a console.
From the site this command should work:
java -jar Azureus2.jar --ui=console

I always get:
```

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
rpr@lt-it-tom:~/.azureus$ cd /usr/share/java/
rpr@lt-it-tom:/usr/share/java$ java -jar Azureus2.jar --ui=console
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
rpr@lt-it-tom:/usr/share/java$ sudo nano -w /usr/bin/azureus 
rpr@lt-it-tom:/usr/share/java$ java -jar Azureus2.jar --ui=console
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine
rpr@lt-it-tom:/usr/share/java$ java -jar Azureus2.jar --ui=console
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine

```
Anyone know how to fix this?

I tried adding the --ui=console to the /usr/bin/azureus but it is always trying to open a bittorent with that name.

---

### Post by Kisil on 2007-04-13
Not to avoid the issue, but why not just use a console-based bittorrent client?  If you're not using the GUI, the java overhead is kind of unnecessary.  Azureus slows my system considerably, and apart from the GUI I don't know that it adds anything a command line bittorrent doesn't do.

---

