---
title: "Update manager not cooperating"
date: 2008-03-23
forum: General Help
---

### Post by power_speed on 2008-03-23
Brand new Install.  7.10

So far only a few minor issues, but one major one.  Update manager keeps giving me endless loops, saying checking for updates.  Then i am presented with the list, when I click install it checks again.  On goes this cycle.

Occasionally,  It will ask for my password.  I enter it and then it will say the sudo protocal does not support this level.

Any ideas to help the newbie,
Thanks in Advance!!!

---

### Post by Ocxic on 2008-03-23
in a terminal do "sudo apt-get update" then "sudo apt-get upgrade"

---

### Post by softwaretech on 2008-03-24
I keep getting these and I'm not sure how to fix them.:confused:

dpkg: error processing ntp (--configure):
 subprocess post-installation script returned error exit status 1
Setting up unzip (5.52-10ubuntu1.1) ...
Errors were encountered while processing:
 cupsys
 hplip
 hpijs
 ntp
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by power_speed on 2008-03-24
I tried the apt get function,  It didn't help.

Here is the error as it appears.

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '48234499' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmphLFE7Q' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

Problem Is I am the administrator.

---

### Post by alexforcefive on 2008-03-24
Are you on an administrator account though?

---

### Post by power_speed on 2008-03-25
I don't know for sure. It didn't give me that option when I installed.

---

