---
title: "System suddenly doesn't power off on shutdown"
date: 2012-11-21
forum: General Help
---

### Post by rdh61 on 2012-11-21
Lubuntu 12.04, Acer Travelmate 4001LMi.

Hi,

Until 2 days ago my system shut down normally.

Since 2 days it doesn't power off. I get the Lubuntu logo and the flashing dots interminably.

Possibly there have been some package updates, I honestly can't remember! The only other thing that's changed is that I upgraded the RAM, but I don't think that could have affected this, could it?

Any help resolving this greatfully received.

Many thanks.

---

### Post by ajgreeny on 2012-11-21
If you use the update manager of Lubuntu rather than using apt-get to update your system you can see what packages have been updated by opening synaptic and going to File ->History.  You will see listed there every date that either synaptic or the update-manager has been used to update your system, and which packages it upgraded.

If you use apt-get in terminal you will need to look through the logs /var/log/dpkg.log.1 and /var/log/dpkg.log.  You can use the command ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
``` to list the lines that are for upgrades and make the list of packages much easier to decipher.

That may give you a clue to any upgrades that could have caused the problem.

---

### Post by rdh61 on 2012-11-22
OK thanks. There were various package upgrades on 18 and 19 November, but I haven't a clue how I would know which of them might be responsible!

---

