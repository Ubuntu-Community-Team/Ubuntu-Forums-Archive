---
title: "How can I make tcptrack autorun?"
date: 2014-01-16
forum: General Help
---

### Post by manas2 on 2014-01-16
Hi :) I am an uber noob in this and was playiing with things around....


I have donwloaded a small tcp sniffing utility named tcptrack.
To execute it I run the command "sudo tcptrack -i eth0" in termial. Then, it shows the connection lists with speeds.

However, I am tired of having to enter it everytime when my sessions starts. So, how can I make it autrorun on each login/boot session?

I have tried it adding to /etc/rc.local and to /etc/init.d/rc.local . 
I am using Ubunti 13.10

Thanks in advance. Have a great day.

---

### Post by manas2 on 2014-01-16
anyone ? :(

---

### Post by ajgreeny on 2014-01-16
When you add it to either of the rc.local files you do not need the **sudo** prefix as both those files are run as root.

However it is also possible that the system is trying to run the commands too quickly after boot, and before networking has configured itself.

Try adding a sleep option of maybe 10 seconds to the command so it becomes **sleep 10; tcptrack -i eth0**

---

