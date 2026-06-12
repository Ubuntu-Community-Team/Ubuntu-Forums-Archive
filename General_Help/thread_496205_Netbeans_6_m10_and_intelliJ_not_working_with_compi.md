---
title: "Netbeans 6 m10 and intelliJ not working with compiz-fusion"
date: 2007-07-08
forum: General Help
---

### Post by Ali_Taimur on 2007-07-08
Hello,

After installing compiz-fusion, i cant seems to use neither Netbeans or IntelliJ. All i see is a grey window. Any idea how to fix that?

---

### Post by Ali_Taimur on 2007-07-12
bump

---

### Post by levele304 on 2007-08-27
experiencing the same problem..


any suggestions?

---

### Post by genxian on 2007-08-27
I have experienced the same problem.  I was able to get Netbeans to install by disabling Compiz-Fusion temporarily (switch back to the default gnome metacity).  After Netbeans was installed I re-enabled Compiz-Fusion and noticed that I could not get Netbeans to launch.  I disabled Compiz-Fusion but Netbeans will stil not launch.  I am stuck now.  Anyone have ideas?

Thanks,

Brandon

---

### Post by SigmundL on 2007-09-21
Add 

AWT_TOOLKIT="MToolkit"

to .bashrc or /etc/environment

/S

---

### Post by cpudney on 2008-05-22
G'day,

I had this problem with _[IntelliJ 6.04 running with JDK6.0u4 on Hardy]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2008/05/compiz-effects-causing-problems-for.html")_.  It's a known bug for Java Swing apps running with Compiz.

I tried setting:

AWT_TOOLKIT=MToolkit

and while this solved the empty dialog windows when Compiz effects were enabled it caused other problems, namely, windows losing keyboard focus (even more annoying than the empty JDialogs).

The _[workaround is to install JDK6.0_u10 beta (build 24)]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2008/05/compiz-effects-causing-problems-for.html")_ and use this to run your Java Swing apps.  In the case of IntelliJ IDEA set JDK_HOME to the path to JDK6.0_u10.

HTH,
Chris.

---

### Post by BARlotta on 2008-07-19
Just installed JDK6u10 (bld27) and haven't seen the empty dialog box issue (at least not yet) - netbeans 6.1.  Thanks for the tip on this.  Hadn't heard that update 10 was fixing this.

---

