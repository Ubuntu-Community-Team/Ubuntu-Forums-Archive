---
title: "Keyboard Shortcut for Non-Responsive programs"
date: 2007-10-21
forum: General Help
---

### Post by LinuxNewb092 on 2007-10-21
Can someone tell me how to terminate non-responsive programs please in Ubuntu 7.10?

---

### Post by thirddeep on 2007-10-21
Option 1:
In a terminal, type "xkill", this will bring a little skull and bones icon up.  Click on the application you wish to kill.

Option 2:
In a terminal, type "ps -ef | grep XXX" where XXX is part of the name of the applications.  For example...
```
ps -ef | grep fox
USER      3096     1  3 Oct20 ?        01:01:52 /usr/lib/firefox/firefox-bin

```
Now kill it with:
```
kill -9 ID
```
Where ID is the first number after the user.

Thd.
p.s. Just noticed that my FF PID is 1, that's strange.

---

### Post by LinuxNewb092 on 2007-10-21
Thank you.

---

