---
title: "ubuntu 20.04 server crashing my home network"
date: 2021-04-15
forum: General Help
---

### Post by murs3051 on 2021-04-15
I am hosting multiple websites on raspberry pi 4 ubuntu 20.04 server where some website are using apache reverse proxy. The problem is when the raspberry pi is connected to home network it runs smoothly but after some times the it is inaccessible and the internet connectivity of my home network also breaks. When I check my main router the earth logo light on it turns to orange instead of being green. If i disconnect raspberry pi or restart the raspberry pi the internet connectivity is back to normal in the home network and the earth logo light is green on my main router. But after some the above issue occurs again and again. I don't know what is causing the issue someone please help!!!

---

### Post by CelticWarrior on 2021-04-15
Welcome.

Hosting websites with a home router is the worst case scenario. Please contact your ISP.

---

### Post by murs3051 on 2021-04-15
Thanks for the reply @CelticWarrior I have no idea what should I ask my ISP ?

---

### Post by murs3051 on 2021-04-15
Should I replace my home router to business router? 
If I have to replace it is mikrotik good for hosting websites?

---

### Post by HermanAB on 2021-04-15
Don't poke around in the dark. Run tcpdump and see what is going on.  There are many misconfiguration possibilities that can lead to packet storms.

---

### Post by QIII on 2021-04-15
What CelticWarrior is saying is that most Internet Service Providers (ISPs) do not allow web servers running on** residential accounts**.  For that, you need more capable -- and expensive -- **commercial/business accounts.**  They may be throttling your throughput when it hits some point.  If they catch on that you are hosting websites, they may either suspend your account or upgrade it to a commercial account and send you a bigger bill.

For my websites, I use a VPS (Virtual Private Server) provider for my virtual machines.  They handle the web access, some of the protection and all of the physical maintenance and uptime requirements.  I administer the virtual machines over ssh.

When I lived in town, my ISP would not allow me to host web servers, even though my service was very fast.  Out here on our farm my bandwidth is limited, so even if my ISP allowed it, I'd not be able to host.

---

### Post by HermanAB on 2021-04-16
Regardless of the type of ISP account, the network should not 'crash'.  Look at the packets with tcpdump or wireshark.  Poking around like a black bear in a coal mine in the dark, is a waste of time.

---

