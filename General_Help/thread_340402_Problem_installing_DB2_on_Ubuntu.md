---
title: "Problem installing DB2 on Ubuntu"
date: 2007-01-17
forum: General Help
---

### Post by Eri on 2007-01-17
Hi,

I have install DB2 Express V9 but:
I have a problem with the db2admin command:](*,) 

dasusr1@eri-desktop:~/das/bin$ ./db2admin start
SQL4401C The DB2 Administration Server encountered an error during startup.

I also get an error with the command: db2cc:

db2inst1@eri-desktop:~$ db2cc
Exception in thread "main" java.lang.NoClassDefFoundError: sun.awt.X11.XToolkit
at java.lang.J9VMInternals.initialize(J9VMInternals.java:127)
at java.lang.Class.forNameImpl(Native Method)
at java.lang.Class.forName(Class.java:131)
at java.awt.Toolkit$2.run(Toolkit.java:864)
at java.security.AccessController.doPrivileged(AccessController.java:191)
at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:847)
at javax.swing.UIManager.initialize(UIManager.java:1296)
at javax.swing.UIManager.maybeInitialize(UIManager.java:1279)
at javax.swing.UIManager.getDefaults(UIManager.java:590)
at javax.swing.UIManager.get(UIManager.java:852)
at com.ibm.db2.tools.common.CommonUIManager.initialize(Unknown Source)
at CC.setLookAndFeel(Unknown Source)
at CC.<init>(Unknown Source)
at CC.main(Unknown Source)
DB2JAVIT : RC = 1

If someone could help me.:D 
Thank you in advance.
Best regards

---

### Post by mxc on 2007-10-24
I have the same problem. Did you solve this in the end? Getting db2 to run without problems is a real task :(

---

