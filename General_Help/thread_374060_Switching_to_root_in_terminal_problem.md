---
title: "Switching to root in terminal problem"
date: 2007-03-02
forum: General Help
---

### Post by RUGUNIT on 2007-03-02
For some reason i cant use the su root command in terminal. I put in my password and it says:

Password: 
su: Authentication failure
Sorry.


Anyone know the solution? Im a newbie as you can probably tell, and im sure the problem will be super simple.

Thanks,

Rug

---

### Post by Gerard Barberi on 2007-03-02
In ubuntu, we use sudo.  Which means something like run the following command as root.

If you want to activate the root account, you could

sudo passwd root

---

### Post by yabbadabbadont on 2007-03-02
To get the same effect as using su, just run "sudo -s -H".  That will drop you into a root shell.

---

### Post by aysiu on 2007-03-02
Ubuntu uses *sudo*, not *su*.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There's absolutely no need to activate the root account or log in as root. yabbadabbadont has a good workaround, though.

---

