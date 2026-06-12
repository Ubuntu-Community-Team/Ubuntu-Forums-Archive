---
title: "[SOLVED] Change link to java"
date: 2007-11-05
forum: General Help
---

### Post by eumetaxas on 2007-11-05
Hi!
i'm using ubuntu 7.10.
When i try to run jpicedt  from terminal (a java app) i gen the followng error
**exec: 4: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java: not found**
Indeed there is no java-6-sun-1.6.0.00 it's
**/usr/lib/jvm/java-6-sun-1.6.0.03**
the app works fine on right click
how can i fix this??
thanks a lot!

---

### Post by laharrin on 2007-11-06
there will be a file in /usr/bin called jpicedt.  you need to open it and edit 1.6.0.00 to say 1.6.0.03

---

### Post by eumetaxas on 2007-11-07
thanks for the answer!
there's no such file in /usr/bin
i've opened the jpicedt.jar with archive manger in /usr/share folder. there are lots of files in it. i did a search in the archive for the key words "usr//lib/jmv..." with no luck.
So for the time i navigate to /usr/share/jpicedt.... and right click to open.

---

### Post by eumetaxas on 2007-11-10
Temporary solution:
Changed permissions of the file jpicedt.jar and open default by java runtime... Made link to start menu and it works fine.
Thanks

---

### Post by Elegorod on 2007-11-10
Enter in terminal
```
which jpicedt
```
Path to shell script will appear. Edit it, replacing java-6-sun-1.6.0.00 with java-6-sun (it's link to java-6-sun-1.6.0.03). If it doesn't contains such path, please, post its content.
Don't edit jpicedt.jar, it contains only application itself, not path to java virtual machine.

---

### Post by eumetaxas on 2007-11-11
!!!!!
thanks!
Solved!

---

