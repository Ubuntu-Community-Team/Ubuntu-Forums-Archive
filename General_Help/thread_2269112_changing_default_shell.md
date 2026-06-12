---
title: "changing default shell"
date: 2015-03-13
forum: General Help
---

### Post by rawlins02 on 2015-03-13
Yesterday I attmpted to change shell to run a script. I prefer tcsh. I believe I did:

```

> chsh -s /bin/csh

```

This changed to csh for the one shell, not any others that I opened.  Today I restarted the machine and now all shells are csh by default. /etc/passwd shows /bin/tcsh. Executing the chsh command with /bin/tcsh returns to the csh prompt. No message saying shell changed.  What am I doing wrong?

---

### Post by rawlins02 on 2015-03-13
SOLVED:  I just needed to log out and in.

---

