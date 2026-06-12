---
title: "eclipse seems to be having trouble with my JVM"
date: 2005-07-01
forum: General Help
---

### Post by Trojan1313 on 2005-07-01
Hello.
I've tried to install the Java Virtual Machine for a while now. I suddenly got it working by installing Azureus with Synaptic.

Still, eclipse gives me this error (an erorr that tells me to go to a file with this text actully):
> 
!SESSION Fri Jul 01 23:48:42 CEST 2005 -----------------------------------------
!ENTRY org.eclipse.core.launcher 4 0 2005-07-01 23:48:42.678
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.RuntimeException: Could not find framework
	at org.eclipse.core.launcher.Main.getBootPath(Main.java:635)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:272)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

And when I ad the Java Free SDK available on Synaptic I get the error that some jar-file is missing, wich it's not.

---

### Post by michael_salcher on 2005-07-01
[QUOTE=Trojan1313]Hello.
I've tried to install the Java Virtual Machine for a while now. I suddenly got it working by installing Azureus with Synaptic.

Still, eclipse gives me this error (an erorr that tells me to go to a file with this text actully):


And when I ad the Java Free SDK available on Synaptic I get the error that some jar-file is missing, wich it's not.[/QUOTE]
 why don't you download the installer from java.sun.com and give that a try?

---

### Post by Trojan1313 on 2005-07-02
[QUOTE=michael_salcher]why don't you download the installer from java.sun.com and give that a try?[/QUOTE]
 Tried it, but it doesn't work, 'cause I have to change $PATH and well, all sorts of things. Have it somewhere on my disc though...

Would there be complications if I tried having both installed?

---

