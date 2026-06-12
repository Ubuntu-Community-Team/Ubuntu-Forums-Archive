---
title: "help! need a better way to configure my Modem"
date: 2006-12-04
forum: General Help
---

### Post by Raval on 2006-12-04
I have an Actiontec EX560LKU USB / Serial modem. Ubuntu does not auto detect the modem but I was able to get it to work following the instructions from this thread [http://ubuntuforums.org/showthread.php?t=220173](http://ubuntuforums.org/showthread.php?t=220173)

using "dmesg | grep USB" I was able to locate the modem at USB0

and using "ln -sf /dev/ttyUSB0 /dev/modem" I was able to substitute the port just like the author of that thread.

problem is I have to substitute the port every time I boot up. Is there a command I can use to permanently configure my modem or under properties under networking that my modem is locates at USB0?

---

### Post by ingo on 2006-12-06
well, I don't know the thread nor the commands, but you could write a bash script that gets started every time you boot or log in.

there should be plenty of stuff on scripts in the forum if you don't know how to do it...

---

### Post by Raval on 2006-12-06
how bout adding USB0 under modem>properties>port

---

