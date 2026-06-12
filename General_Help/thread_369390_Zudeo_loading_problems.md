---
title: "Zudeo loading problems"
date: 2007-02-24
forum: General Help
---

### Post by Webspot on 2007-02-24
When trying to run the zudeo client, which I downloaded from zudeo.com, I get this error:

```

Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading Azureus:
./azureus: line 108: cd: /home/andrew/Apps/Azureus: No such file or directory
java -Xms16m -Xmx128m -cp "/home/andrew/Apps/Azureus:Zudeo/*.jar" -Djava.library.path="/home/andrew/Apps/Azureus Zudeo" -Dazureus.install.path="/home/andrew/Apps/Azureus Zudeo" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/ui/swt/Main
Azureus TERMINATED.

```

I had azureus working before, but I would have liked to try out the zudeo stuff.

Any ideas on what to try to do?

Thanks

---

### Post by UltimaDude on 2007-02-24
Are you sure you directly linked to the file, thats all I can think of,
I'm already having trouble with Ubuntu 6.06 after restarting then QEMU would stall.

---

