---
title: "printer prints by itself"
date: 2015-06-18
forum: General Help
---

### Post by cmcanulty on 2015-06-18
This is an HP LaserJet P2035n. Lately most nights it prints page after page of this; one page says just 

"GET / HTTP/1.0"

then the next page says


"OPTIONS / RTSP/1.0"

over and over. I have this at a library and it is connected by Ethernet to the system and used by 12 Xubuntu 14.04 64bit computers. I have emptied the printer queue on all computers and also reinstalled it on all. HP forums had a post about this in 2009 but no answers. our library is very poor and we hate to waste all this paper and toner. Documents print fine.

[http://h30499.www3.hp.com/t5/Black-and-White/LaserJet-4000-Prints-out-quot-HEAD-HTTP-1-0-quot-or-quot-Get/td-p/4394597?notmigrated#.VYMiQbyMb0u]("http://h30499.www3.hp.com/t5/Black-and-White/LaserJet-4000-Prints-out-quot-HEAD-HTTP-1-0-quot-or-quot-Get/td-p/4394597?notmigrated#.VYMiQbyMb0u")

---

### Post by JKyleOKC on 2015-06-19
My best guess is that the printer's IP address has somehow become listed in a DNS server somewhere as a web server (such as apache), and one of the search spiders or Random J. Hacker is attempting to access it.

If you're administering the system, and using *iptables* to implement its firewall, you can add a rule there to log every packet addressed to the printer's address, and this may help you identify from where the requests are coming. You could then put a rule in to block those requests, or possibly to block all packets addressed to the printer at any of the HTTP ports.

As I said, these are simply guesses, based on having dealt with HTTP packet exchanges for more than 20 years now, and with printers doing strange and wonderful but mysterious things for no obvious reason... Hope they help, and be sure to let us know what happens next.

---

### Post by cmcanulty on 2015-06-20
I run the system and would like to try what you suggest but am not good enough to know how to do that. We don't run a server, each machine is administered individually. Our catalog system is evergreen and the server for our library and many others is from evergreen in Grand Rapids. I administer the router.

---

### Post by pfeiffep on 2015-06-20
> **cmcanulty said:**
> I run the system and would like to try what you suggest but am not good enough to know how to do that. We don't run a server, each machine is administered individually. Our catalog system is evergreen and the server for our library and many others is from evergreen in Grand Rapids. I administer the router.I might be suggesting the obvious here ... turn off the printer until you find a more elegant solution such as the one suggested by JKyleOKC. 
Have you explored hplip (software I use to control my HP printer) for solutions?

---

### Post by cmcanulty on 2015-06-20
I have hplip installed on everything but never knew it did anything besides make the printer print

---

### Post by JKyleOKC on 2015-06-22
> **cmcanulty said:**
> I run the system and would like to try what you suggest but am not good enough to know how to do that. We don't run a server, each machine is administered individually. Our catalog system is evergreen and the server for our library and many others is from evergreen in Grand Rapids. I administer the router.Since I'm not familiar with that specific HP model, I don't know what capabilities exist in its control software. My suggestion made the assumption that you had a local box acting as a print server, with all print jobs routed through it on their way to the printer. Since you don't have that setup, it's probably a red herring...

The suggestion by  **pfeiffep** to use the hplip utility to check printer settings is probably your best bet. It **may** be able to block incoming traffic from specific IP addresses -- and you may be able to tell from the router's internal logs where the unwanted print jobs are coming from. That might be a permanent solution.

The hplip utility is pretty powerful!

---

### Post by cmcanulty on 2015-06-22
OK will do and will let you know, I work at library tomorrow and Thursday

---

