---
title: "Power button freezes Gurtsy!"
date: 2007-10-20
forum: General Help
---

### Post by saz on 2007-10-20
Hi ppz!

Just installed Gutsy and got the wireless to work.. but now i have to deal with a different problem.. whenever i press the "quit" button Ubuntu freezes,,, and i have to either restart X and shutdown from login screen, or ctrl+alt+f1 and shutdown from the command line..

pls could anyone help with this?

---

### Post by saz on 2007-10-20
anyone pls??

---

### Post by Jexel on 2007-11-24
i have the exact same problem...does anybody know what's wrong?

---

### Post by Jexel on 2007-11-24
Seems like this bug has been reported...

[https://bugs.launchpad.net/ubuntu/+bug/150846](https://bugs.launchpad.net/ubuntu/+bug/150846)

None of the suggested workarounds works for me though...

---

### Post by Jexel on 2007-11-24
After digging around I found the problem, here's my solution
In terminal type:
```
sudo gedit /etc/init.d/rc
```

And change the line:
```
CONCURRENCY=shell
```
to
```
CONCURRENCY=none
```

I had changed it to shell hoping that it would speed up my boot time but it has caused more problems than it's solved...

hope this helps...

---

### Post by saz on 2008-03-27
i'm sorry you discovered that only after i'd a fresh install xD thanks anyway!

---

