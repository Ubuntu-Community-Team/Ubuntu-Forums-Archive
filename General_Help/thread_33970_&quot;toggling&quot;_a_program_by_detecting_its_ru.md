---
title: "&quot;toggling&quot; a program by detecting its running status"
date: 2005-05-12
forum: General Help
---

### Post by 23meg on 2005-05-12
i'd like to have a script/app that will do the following:

- on launch, check if a particular application is running
- if it's running, kill it, and quit
- if it's not running, start it, and quit

it must be a trivial matter to do this with bash, but i don't know what command to use to detect the running / not running status of a specific app. i've found "watchdog" daemons that do this, but they don't perform the check on launch, rather they will keep running and monitor the application in certain intervals, which is overkill for my purpose.

any ideas? 

(maybe this should have gone in to the programming section, since it's probably going to be achieved using a bash script, but i'm not entirely sure..)

---

### Post by tread on 2005-05-13
Here's a cheap little script:
```

#!/bin/bash
ps -e | grep xterm
x=$?;
if [ $x -eq 1 ]; then
        xterm
else
        killall -9 xterm
fi

```

---

### Post by 23meg on 2005-05-13
wow, you rock sir! just replaced your "xterm" with my custom Eterm command line from the Eterm fonts thread, and i'm in terminal heaven! you made my day, thanks a lot.

---

### Post by tread on 2005-05-13
Hehe .. you are welcome! Besides, that post gave me a caffeine drip  \\:D/

---

### Post by 23meg on 2005-05-13
congrats, and keep up the helpful posts..

---

