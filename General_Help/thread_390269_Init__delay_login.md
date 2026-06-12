---
title: "Init : delay login"
date: 2007-03-21
forum: General Help
---

### Post by f3d on 2007-03-21
Hi there,

Usplash is great but I do like booting in text mode... :rolleyes: 
Unlike what you can see in the provided image, I'd like to have login not be spawn between the rcS.d and the rc2.d scripts which makes the rest of the output all messed up. I'd like login to appear when all scripts are done. I looked at /etc/event.d and /etc/init.d/rc and didn't find where that behaviour could be configured, so if anybody could help that would be much appreciated.

Greetings.

---

### Post by energiya on 2007-03-22
I also like the text mode booting better...
Are you using InitNG or any parallel method of booting? I just can't remember the order Ubuntu reads and executes instructions from the init scripts.

---

### Post by f3d on 2007-03-22
I got the default init system which is upstart. First your rcS.d scripts are executed followed by your default runlevel ones (rc2.d). In /etc/init.d/rc concurrency is set to none. I didn't find where you could tell login to be the last command executed.

Edit :

I've just find a way to do what I wanted (cf. [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html))

In /etc/event.d/tty1 I replaced :

```
start on runlevel 2
```

by 

```
start on ze_end
```

and added a script named S99ze_end in rc2.d containing :

```
#!/bin/bash

initctl -q emit ze_end
```

---

