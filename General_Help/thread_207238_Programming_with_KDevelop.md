---
title: "Programming with KDevelop"
date: 2006-07-01
forum: General Help
---

### Post by SPlutard on 2006-07-01
Well, I'm reasonably versed in C/C++, and am learning Java so I need to be able to write/compile/run programs (obviously) and, naturally, would like to do all that with Linux. 

I've tried simple programs in both languages, but I can't get either to compile, much less run. So, I'm wondering if there was anything special I needed to download to be able to use either language correctly (like libraries, or the Linux equivalent of Java's JVM/IDE)?

I could post the complete compilation text readout, but it is rather long. If it would help, I'm happy to, but I didn't want to clutter things up if this is something simple that I'm overlooking.

Or, on the other hand - is there a more effective app to use instead of KDevelop that might  eliminate these problems (if any?)?

Thanks,
SP

---

### Post by SPlutard on 2006-07-01
Here's the compile error from a Java program (which happens to be much shorter than that of a C/C++ program):
```
VisualBoyAdvance /home/lucas/docs/Docs./Programming/Java/javatest/
/bin/sh: VisualBoyAdvance: command not found
*** Exited with status: 127 ***
```

---

### Post by ifokkema on 2006-07-01
You need to install some packages to be able to compile. For C, you need:
```
sudo apt-get install build-essential
```
For Java, you need:
```
sudo apt-get install j2sdk1.4
```

---

### Post by SPlutard on 2006-07-02
Cool - thanks. I figured it would be something simple like that. 

'Preciate it!
SP

---

