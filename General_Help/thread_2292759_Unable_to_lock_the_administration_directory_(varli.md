---
title: "Unable to lock the administration directory (/var/lib/dpkg/)"
date: 2015-08-30
forum: General Help
---

### Post by Harry_Riley on 2015-08-30
Hi, I am running Ubuntu 15.04 on a Lenovo T550 and every time I run apt-get update command I get:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This was after unsuccessfully trying to install Mutt.

How can I resolve this?

Harry

---

### Post by lisati on 2015-08-30
Do you have the software centre or update manager open when trying to run apt-get?

---

### Post by Harry_Riley on 2015-08-30
No the only thing open is chrome.

---

### Post by lisati on 2015-08-30
> **Harry_Riley said:**
> No the only thing open is chrome.

Odd. "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" commonly appears only when something that can install, update or remove software is already running. I shall have to defer to the wisdom of others for troubleshooting tips.

---

### Post by Harry_Riley on 2015-08-30
I seem to have resolve the issue by restarting the computer.  When I ran the update command it told me to run a sudo dpkg command to fix the problem.

---

### Post by Harry_Riley on 2015-08-30
This was the command "sudo dpkg --configure -a"

---

### Post by ian-weisser on 2015-08-31
> **Harry_Riley said:**
> When I ran the update command it told me to run a sudo dpkg command to fix the problem.
[...]
This was the command "sudo dpkg --configure -a"

That message is expected when you restart (or shutdown) while dpkg is locked.
Obey the instruction and run the command.

---

### Post by flaymond on 2015-08-31
This issue always happening to me, whenever I ***accidently ***deleted a terminal window while the terminal running apt-get command. Common way to resolve this is by restarting, but I'm just directly launch ***top ***and find ***apt-get ***running task id, and delete it with ***kill <ID>***. However, I don't think by killing is safe, because you sometimes can kill another process, again ***accidently.***

 You should run ***sudo dpkg --configure -a***&#8203; after rebooting to fix the involved previous task.

---

### Post by Harry_Riley on 2015-08-31
Thank You!

---

