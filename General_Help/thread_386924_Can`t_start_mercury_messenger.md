---
title: "Can`t start mercury messenger"
date: 2007-03-17
forum: General Help
---

### Post by remiandre on 2007-03-17
I have problem opening my mercury messenger

When I type mercury in the terminal I get this message

```
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: defaultCloseOperation must be one of: DO_NOTHING_ON_CLOSE, HIDE_ON_CLOSE, or DISPOSE_ON_CLOSE
        at javax.swing.JDialog.setDefaultCloseOperation(JDialog.java:705)
        at org.1.13.0.0(Unknown Source)
        at org.1.13.0.1(Unknown Source)
        at org.1.13.3.run(Unknown Source)
        at org.1.13.0.handleException(Unknown Source)
        at org.1.13.0.0(Unknown Source)
        at org.0.2.0.main(Unknown Source)
        at com.dMSN.Main.main(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)

```

---

### Post by peabody on 2007-03-17
Seems to be a java problem, is this a piece of software that's in Ubuntu's repositories or did you install it yourself?  I've never heard of Mercury messenger before.  If it's not in Ubuntu's repositories, you may need to get support from where ever the software is distributed from.

---

