---
title: "Running script as root at startup Ubuntu 19.04"
date: 2019-06-25
forum: General Help
---

### Post by mysticduck on 2019-06-25
I needed to run

```
modprobe -r lp
```

at startup so Virtualbox could grab the parallel port.  I made a script "unload lp.sh" with the above code, ran chmod u+x on it to make it executable, put it into startup applications and restarted, no joy.  After some searching I tried adding

```
#!/bin/bash
```

to the beginning of the script, also no joy, but if I ran the script from terminal it worked as expected.  I fixed my issue by creating /etc/rc.local and putting the modprobe in there, but I'm curious why it didn't work through startup applications.  This is purely for my edification, I like knowing how and why stuff does (or doesn't) work.  

 

Thanks!

---

### Post by sisco311 on 2019-06-25
[s]Add `lp' to the /etc/modules file.[/s]
[https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

EDIT: Oh, you have to remove the module. You can blacklist it in /etc/modprobe.d/blacklist:
```

blacklist lp
```

---

### Post by mysticduck on 2019-06-25
That info was what I was looking for before I started making the script, thanks!  I am however still curious why my method didn't work, more for future reference than anything else.

---

### Post by sisco311 on 2019-06-25
"startup applications" are automatically launched during startup of the user's desktop environment after the user has logged in, but modprobe must be run as root.
See: [https://specifications.freedesktop.org/autostart-spec/autostart-spec-latest.html](https://specifications.freedesktop.org/autostart-spec/autostart-spec-latest.html)

Putting the command in /etc/rc.local should be avoided. The file is executed by [systemd]("https://en.wikipedia.org/wiki/Systemd") for backward compatibility with [sysvinit]("https://en.wikipedia.org/wiki/Init#SysV-style") but you can't predict at which point of the booting process is executed.

---

### Post by mysticduck on 2019-06-25
Gotcha, I was under the assumption startup applications were run as root.  I'll do the blacklist like you mentioned, thanks for all the help and information!

---

