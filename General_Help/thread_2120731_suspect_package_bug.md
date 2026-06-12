---
title: "suspect package bug"
date: 2013-02-27
forum: General Help
---

### Post by pfeiffep on 2013-02-27
How do I report a suspected package bug?

---

### Post by dino99 on 2013-02-27
from a terminal, run:

ubuntu-bug thatsuspectpackagename

apport will perform the needed operations, open the launchpad bugs account you might have, then post some details that can help the devs to understand the issue.

---

### Post by pfeiffep on 2013-02-27
> **dino99 said:**
> from a terminal, run:

ubuntu-bug thatsuspectpackagename

apport will perform the needed operations, open the launchpad bugs account you might have, then post some details that can help the devs to understand the issue.

Thanks, however that actually didn't do anything; I did however go to [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) and discovered that this 'error' has been reported previously (4.3.2012)

I added my info there - hopefully this will get the package correct attention.:KS

---

### Post by deadflowr on 2013-02-27
Can you provide us with any info on the bug?
I would hate to come across the same bug, report it and end up with a dupe bug report.

---

### Post by pfeiffep on 2013-02-27
> **deadflowr said:**
> Can you provide us with any info on the bug?
I would hate to come across the same bug, report it and end up with a dupe bug report.
bug #972693
Involves incorrect command to fix virtual box
VB installs then when setting up first environment fails with a suggestion to run command
[INDENT]/etc/init.d/vboxdrv setup[/INDENT]

):PIn fact the correct command is 
[INDENT]/etc/init.d/virtualbox setup[/INDENT]

---

