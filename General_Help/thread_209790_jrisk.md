---
title: "jrisk"
date: 2006-07-05
forum: General Help
---

### Post by zorkerz on 2006-07-05
Does anyone know how to install jrisk.  It looks like a cool version of risk and the applet works very nicely.  However I would like to be able to play offline.  Im also thinking of trying to make some of my own maps for it.
Thanks a bunch
elias

---

### Post by zorkerz on 2008-03-10
Can anyone recommend a working version of java for running jrisk in ubuntu hardy 64 bit. Ive tried icedtea-java7 and sun-java6 but can get Risk.jar to start.
thanks

---

### Post by zorkerz on 2008-03-16
ok so i have now installed sun-java6 and can start risk by right clicking Risk.jar and selecting Open with "Sun Java 6 Runtime".

Im trying to make my own map using SwingGUI but i don't know how to open it. I believe the following command should open it ```
java -cp Risk.jar risk.ui.SwingGUI.SwingGUIFrame
```

However I get the error > The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * icedtea-java7-bin
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


So it seems that sun-java6-jre either gets assigned a command other than java or it not benig assigned at all.

Does anyone know how to get around this?

---

### Post by zorkerz on 2008-03-21
problem solved now. I reinstalled hardy for other reason and am ok now. 
Not sure why I keep writing to myself.
 :~)

---

### Post by sajro on 2008-03-21
That was a long time to figure it out. eh?

---

### Post by zorkerz on 2008-03-21
I really only made sporadic attempts to fix it

---

