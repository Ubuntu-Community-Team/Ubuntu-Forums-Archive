---
title: "configure, make, and make install log outputs"
date: 2007-11-12
forum: General Help
---

### Post by alnhntr29 on 2007-11-12
Can somebody tell me where the output files get stored at when you use configure, make and make install to compile something? Thnx in advance.

---

### Post by taurus on 2007-11-12
I believe ./configure will be logged in configure.log.  Otherwise, it will print on a terminal or screen when you run the command.

---

### Post by geirha on 2007-11-12
configure will log some information to config.log, but other than that, nothing gets logged. It's something you do yourself if you want it. Like: 
```

./configure 2>&1 | tee configure-prog.log
make 2>&1 | tee make-prog.log
make install 2>&1 | tee install-prog.log

```

---

### Post by alnhntr29 on 2007-11-12
This code is what i would type to get a log of it? Just as you typed it?

---

### Post by geirha on 2007-11-12
More general: if you run a command, and you want to capture all the data it outputs, you put ```
2>&1 | tee some-log-file.log
``` behind it

---

