---
title: "Boot drops to shell on Ubuntu 7.04"
date: 2007-07-09
forum: General Help
---

### Post by graverisen on 2007-07-09
Hi all,

My name is Leandro, I'm from Brazil and new to Ubuntu and Linux in general.
after an upgrade from Ubuntu 6.10 to 7.04 every time the system boots it shows the progress bar and after a little while it drops to a shell. It happens always after the "configuring network interfaces.....[ok]" but there's no error message. In this shell, if I enter the "exit" command the boot finishes just fine and I don't notice any problems operating the system.

How do I find out what's wrong? :confused:

---

### Post by graverisen on 2007-07-10
Can't anyone help me? At least point to the relevant logs so I can try to solve the problem?

---

### Post by CheShA on 2007-07-10
I'd hazard a guess there is some issue with the old Ubuntu using init to start all services  and new ubuntu using upstart  instead.. Unfortunately I'm new to upstart myself so I can;t really give any more advice.

---

### Post by graverisen on 2007-07-10
Since I'm new to Ubuntu, I went where I think I must go, pleae correct me if I'm wrong, but I've checked /var/logs/boot and it show a error in one line:

rcS: error: "sudo su -c 'echo dev.rtc.max-user-freq" is an unknown key

Is this related? How do I fix it?

---

