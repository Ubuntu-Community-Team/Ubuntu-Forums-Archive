---
title: "how to kill crashed firefox"
date: 2014-04-02
forum: General Help
---

### Post by Hodor on 2014-04-02
Hi
I'm using some sample Java applets and occasionally do something silly that crashes firefox (e.g. try to open a html file pointing to the .class file without having compiled that first) - firefox hangs, but after I close it its still runing somewhere in the background, gives me an error message (saying its still running and I need to stop it or restart the system).
I've tried looking for the process via ps -aux - but the list is long (and I can't quite rember/too lazy to look up the regular expression to grab the firefox /? mozilla processes)'
So how exactly do I get the process number process number to kill -9 xxx (because I'm tired of rebooting).
Thanks

---

### Post by Dave_L on 2014-04-02
You could use the "top" command, and then use the "k" subcommand to kill it.

Or locate the PID with:

```
ps aux | grep firefox
```

---

