---
title: "bash: /usr/bin/nemo: cannot execute binary file"
date: 2014-04-09
forum: General Help
---

### Post by Redalien0304 on 2014-04-09
bash: /usr/bin/nemo: cannot execute binary file
got this message after making a Copy of my Partition Via Gparted to another drive. Also changed UUid.
so cannot start Nemo Gui or in terminal. Any help is Appreciated Thanks.

---

### Post by slickymaster on 2014-04-09
Usually that error message means Linux doesn't recognize the file as a shell script or as an executable file.

Typically the cause is running an executable on the wrong architecture - if you try to run x86 executables on an ARM CPU, this message comes up.

---

### Post by Redalien0304 on 2014-04-09
ok it is the same Laptop just different Hard drive.

---

### Post by slickymaster on 2014-04-09
I'm just wild guessing here but, maybe because you changed your UUID, Nemo is trying to execute **/bin/id** to get your UUID, which fails, causing the error and terminating the script before it can set up your $PATH.
Because your $PATH is not set, bash is only able to run commands with the full path specified.
You could try to ```
export PATH=/bin:/usr/bin:/sbin:/usr/sbin
``` to fix the $PATH to see if that helps you.

---

### Post by Redalien0304 on 2014-04-11
Marked as Solved cause i think it was part of my Hdd going bad. Also switched to another Hdd.

---

