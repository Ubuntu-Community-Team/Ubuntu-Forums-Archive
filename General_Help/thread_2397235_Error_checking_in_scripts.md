---
title: "Error checking in scripts"
date: 2018-07-26
forum: General Help
---

### Post by raleigh3 on 2018-07-26
Is it a good idea to have these with my cp commands?

```
if [ "$?" != "0" ]; then
    echo "[Error] copy failed!" 1>&2
    exit 1
fi

```

---

### Post by TheFu on 2018-07-27
Error checking and error prevention are always good.   Don't forget to clean up any temporary files by catching signals.   You might want to print the error code  and filenames out, so that someone can look it up.  It is common to see error 13 -permission denied, for example.  I use ERROR:  WARNING: and INFO: in my different messages. Makes grep easier.  Using brackets looks nice, but complicates regex just a little.

---

### Post by raleigh3 on 2018-07-27
I do not understand how to clean up temp files or what catching signals are.

---

### Post by TheFu on 2018-07-27
If your script makes any temp files, then it should clean them up, regardless of how the script ends or crashes. It is common to have a cleanup() function that does this. [http://redsymbol.net/articles/bash-exit-traps/](http://redsymbol.net/articles/bash-exit-traps/)

Signals are ways that different parts of the OS can communicated with other parts.  If you press cntl-c, that sends a signal to terminate a running process.  If the running process is your script, there are a few signals you might want to catch, so you can run the cleanup() function and gracefully die.  Scripts that process DB data or text files often will use temporary files. [http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_12.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_12.html)

---

### Post by raleigh3 on 2018-07-27
Thanks for the cleanup link. Looks very useful.

---

### Post by TheFu on 2018-07-27
Actually, the tldp.org link is probably better, much better. There are beginner and advance Bash Scripting Guides which are full of amazing information there.

---

