---
title: "cupsd"
date: 2012-12-18
forum: General Help
---

### Post by Pedroski55 on 2012-12-18
In Ubuntu 12.04, what would be the command line to start and stop cupsd after changing the printer driver please??

Or rather, to restart cupsd?

---

### Post by Doug S on 2012-12-18
the ubuntu 12.04 server guide says:```

sudo /etc/init.d/cups restart

```

---

### Post by Pedroski55 on 2012-12-18
Tried that, it told me off, it said I should use:

pedro@pedro-bedro:~$ sudo service cups restart 

So I got it in the end!

---

### Post by Doug S on 2012-12-21
Thanks for reporting back.
I was going to enter a launchpad bug report, but I see that the older style "sudo /etc/init.d/XXXX restart" have been changed to "sudo service XXXX restart" in the 12.10 server guide. I think it would still be worth back fixing in the 12.04 (LTS) guide, and I might do that sometime in the next few months.

---

