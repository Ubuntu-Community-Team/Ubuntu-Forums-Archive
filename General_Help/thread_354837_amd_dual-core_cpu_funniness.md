---
title: "amd dual-core cpu funniness"
date: 2007-02-06
forum: General Help
---

### Post by rabidrabbit on 2007-02-06
Under the system monitor it shows only one cpu. I remember under dapper that it had an icon for both cpus and showed their individual load. Did my install somehow only pickup and utilize on cpu?

Ubuntu 6.10
Epox 9npa+SLI
x2 3800
2x1gb ddr400 cas 2236

---

### Post by Ramses de Norre on 2007-02-06
Which kernel do you run? What's in /proc/cpuinfo?

---

### Post by rabidrabbit on 2007-02-06
nothing is in cpu info, i am running kernel 2.6.17-10

---

### Post by Maestro23 on 2007-02-06
> **rabidrabbit said:**
> nothing is in cpu info, i am running kernel 2.6.17-10

#cat /proc/cpuinfo

Hmm... Should see info on one/both of your processors.

Running dual-core AMD myself with 6.10 and it sees both of my processors.

---

### Post by rabidrabbit on 2007-02-06
how about installing the amd processor drivers, i have the files, but how do i install them?

---

### Post by Maestro23 on 2007-02-06
> **rabidrabbit said:**
> how about installing the amd processor drivers, i have the files, but how do i install them?

I dual-boot with XP and had them installed on that side of the house before I installed Ubuntu.  Don't know if that played a part in Ubuntu recognizing them on install.

If you just have Ubuntu installed, then you will need the linux drivers from the AMD site.  Should be a .tar file.  Open a terminal and type #man tar  -will show you how to use the command if you don't know already.

---

