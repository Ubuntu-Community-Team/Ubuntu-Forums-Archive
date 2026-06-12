---
title: "Kubuntu crashes- can't open netowrk socket"
date: 2006-11-13
forum: General Help
---

### Post by keyo on 2006-11-13
Kubuntu will crash while i'm browsing(on FF, opera) and after reboot this error is displayed.
[COLOR="Green"]There was an error setting up inter-process communications for KDE. The message returned by the the system was:
Could not open network socket
Please check that the "dcopserver" program is running![/COLOR]
This will usually occur on a particular web page but it is sometimes random. As far as i can see this is not because of any particular browser or plugin.

System info:
AMD Athlon 64 1.9Ghz
768MB RAM
Marvell/Youkon network chip on ASUS A8V
Kubuntu 6.06 Dapper with Beryl/xgl

---

### Post by mayonaise15 on 2006-11-14
I did some research on this and it could be a permissions error.  Could you type the following into a terminal and post the results please?

```
ls -al ~
```

---

