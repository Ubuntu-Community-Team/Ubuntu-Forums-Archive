---
title: "How do I identify unnecessary processes running in the background and disable them?"
date: 2015-01-27
forum: General Help
---

### Post by arroy_0209 on 2015-01-27
In a new laptop I have installed lubuntu based on ubuntu 14.04.1 and it is advised that unnecessary processes running in the background be stopped to save battery backup duration. How do I identify those processes and disable them? I know that stopping a necessary process by mistake can be extremely harmful so may be keeping processes undisturbed may be good but increasing battery backup time is also necessary. So how do I proceed?

---

### Post by HermanAB on 2015-01-27
The easies method is probably using htop.

---

### Post by Bucky Ball on 2015-01-27
You could also check in 'Session and Startup' and see what you have starting at boot.

---

### Post by ibjsb4 on 2015-01-27
Or

Open up your System Monitor and go to Processes.  From there you can kill any running process and see what effect it has on your system.  If you bork your system a reboot will restore you to default.

Also check out 'powertop'.
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by ajgreeny on 2015-01-27
You could also install **bum** (BootUpManager) and use that to stop any services that are definitely not needed.

But take some care as some services that you think are unnecessary may actually be needed by something else that you do want or need.

---

### Post by kjohri on 2015-01-29
Run [htop]("http://www.softprayog.in/tutorials/htop-command-in-linux"). It will give you a fair idea what processes are running and how much system resources each process is using.

---

