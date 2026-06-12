---
title: "How do I kill a startup application on logout?"
date: 2014-10-25
forum: General Help
---

### Post by speartip on 2014-10-25
I always use a program called redshift on all my linux installs.
On Ubuntu 14.04 I have added it to my startup applications, using the command "/usr/bin/redshift".
Everytime I logout & in again though another instance of redshift starts up.
So if I logout & in 5 times I then have 5 instances of redshift running in my system monitor.
This doesn't seem to happen to any other program, only redshift.
Any suggestions what I can do about this?

---

### Post by VH-BIL on 2014-10-25
Add a script to your startup instead of the program.

```
#!/bin/bash
killall redshift
redshift
```

save that code to a text file somewhere, make it executable and add that to you start programs.

It will kill any existing instances before launching a new one.

---

### Post by speartip on 2014-10-25
Thanks, VH-BIL, That Worked.

---

