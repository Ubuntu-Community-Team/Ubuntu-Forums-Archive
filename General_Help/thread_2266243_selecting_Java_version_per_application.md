---
title: "selecting Java version per application"
date: 2015-02-21
forum: General Help
---

### Post by Fire Raven on 2015-02-21
I have been using Java 6 as my default version because two applications were known not to work in 7/8. One has been upgraded (finally). The other I no longer need (found a non-Java alternative). I want to keep Java 6 installed while I test applications under 8. Probably everything will be ok and I can uninstall Java 6. But if I do still need 6, how can I run a specific application under 6 while 8 is my default version?

---

### Post by TheFu on 2015-02-21
Don't know how to do it the "ubuntu way", but ....

All programs care about 2 environment variables - PATH and LD_LIBRARY_PATH  - you can create a little script that sets those and called the program you like.
Java programs also care about the JAVA_HOME environment variable, so just set that.
So, something like this:
```

#!/bin/sh

export JAVA_HOME=/opt/java1.6.3.34.23.2
export PATH=$JAVA_HOME/bin:$PATH
export LD_LIBRARY_PATH= $JAVA_HOME/lib:$LD_LIBRARY_PATH
# run the program here
java some-java-program opt1 opt2 opt3 ....
```

For the other program, just change the JAVA_HOME and that should work too.  For other source-installed programs, they generally have all their files under a program_home/ directory ... so this same idea works.  It is only when the distro developers got involved that putting settings away from libraries away from programs away from logfiles happened. There are good reasons for that ... but it makes the script above a little longer and more complex.

Anyway - hope this helps.

---

