---
title: "[SOLVED] Startup programs on Awesome WM"
date: 2007-12-23
forum: General Help
---

### Post by corney91 on 2007-12-23
Does anyone know how to add programs to the startup of Awesome?

---

### Post by corney91 on 2007-12-24
Anyone???

---

### Post by cevans on 2008-03-22
Behold the absurdly late reply!

The way one generally does this is to write a script in ~/.xsession that starts whatever one wants, instead of just selecting Awesome in gdm. For example

```

#!/bin/sh

program1 &
program2 &

awesome

```

---

### Post by corney91 on 2008-03-22
Haha, extremely late :D
Thanks for the reply. I had, in fact, worked it out from [this thread]("http://ubuntuforums.org/showthread.php?t=678902"), but hadn't marked this as SOLVED - thanks for reminding me ;)

---

