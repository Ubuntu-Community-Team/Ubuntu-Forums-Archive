---
title: "Edit firewall file via windows"
date: 2014-10-28
forum: General Help
---

### Post by smellslikeyoda on 2014-10-28
Hello all,

I am fairly new to linux, so please be gentle (I am a tech support engineer and am very active in the IT industry so not too gentle :p). Long story short, I have an Amazon aws instance and I apparently (don't know how) disabled port 22...so now I can't ssh into into. I did create a windows instance and have attached the volume to it. Here are my questions:

-First, what program, if any, is suggested for opening linux files in Windows for read/write access?
-Second, which file do I need to edit to open port 22? I used a program to *view* the linux files and saw a few "before" and "after" firewall rule files. Not sure if I need to add something to the before boot file or after. Or is there just a master file that I can edit?

Sorry if this is redundant.

Thank you!

Mike

---

### Post by JazzPotato on 2014-10-28
Never used amazon aws myself, but if you contact amazon tech support they can probably help you. Seems unlikely to me that you will have managed to close access to a port on a hosted vps, maybe you've just disabled the ssh service or uninstalled the ssh server?

---

### Post by smellslikeyoda on 2014-10-28
Hello Jazz,

Thank you for the reply. I already contacted them and they mentioned creating a new instance and attaching the volume to it to view the log files. I am not sure which log files they mean. I was looking at the firewall files that I could find and did not see any mention of port 22 being open. Also, I am not able to telnet to it, so I did not even bother checking services. Just so I can rule it out, any chance you can point me to a config file that will tell me which services are enabled?

---

