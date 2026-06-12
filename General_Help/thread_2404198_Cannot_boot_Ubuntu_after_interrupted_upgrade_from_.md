---
title: "Cannot boot Ubuntu after interrupted upgrade from 16.04 to 18.04"
date: 2018-10-21
forum: General Help
---

### Post by fiyindaniel on 2018-10-21
My computer went off during an upgrade from 16.04 to 18.04 LTS and I haven't been able to get past the login screen successfully.  The screen just goes blank. I learnt trying to use the command dpkg --configure -a works but i havent been able to gain access to the terminal at all. I also can't reinstall the OS from a live CD because it keeps saying 'unable to mount root fs on unknown block'.

---

### Post by oldos2er on 2018-10-21
Can you boot into recovery mode?

---

### Post by fiyindaniel on 2018-10-21
Yes I can. It hasn't proved helpful though. I tried selecting dpkg in recovery mode and I encountered the error invoke-rc.d: could not determine current runlevel.

I selected the root option while in read/write mode and I ran the command dpkg --configure -a and it hasn't solved the problem.

---

### Post by HermanAB on 2018-10-21
I think that you should consider making a backup of your data and re-installing from scratch.  That will be much easier and less time consuming that trying to sort out the mess left by a broken install.

---

### Post by fiyindaniel on 2018-10-21
Oh ok thanks... I've done that but my Wi-Fi adapter isn't working anymore. How can i fix this pls??

---

