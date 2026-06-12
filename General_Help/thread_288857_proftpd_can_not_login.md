---
title: "proftpd can not login"
date: 2006-10-30
forum: General Help
---

### Post by mitjab on 2006-10-30
I have problem with proftpd. I can not login if i am out of the LAN. In LAN works. Ports from 0 to 1024 are blocked by my ISP becouse of this i use 

# Port 21 is the standard FTP port.
Port                            2121

and data port is 20 which is also blocked so i am using

PassivePorts 51000 51999

but i still can not connect to ftp!

If i look on iptraf i see this

[IMG]http://shrani.si/files/slika9FCW.jpg[/IMG]

anyone can help me?

---

### Post by dannyboy79 on 2006-10-30
do you have a router? have you forwarded the applicable ports thtat you have chosen from your router to your server? also, if you are trying to connect from work, I know my company blocks traffic OUTBOUND on most ports that aren't std so I have to use port 21 for my ftp server! I wish I could help but other than the router issue I don't know what else to tell you? Also, if iptraf in the repos? What can iptraf all be used for? It looks like something I'd like to learn how to use!

---

