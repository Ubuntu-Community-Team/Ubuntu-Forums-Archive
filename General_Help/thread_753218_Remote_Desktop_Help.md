---
title: "Remote Desktop Help"
date: 2008-04-12
forum: General Help
---

### Post by Christian Christiansen on 2008-04-12
I want to access my ubuntu 7.10 desktop from my windows 2000 laptop. I've got tightvnc and realvnc installed on both but I still can't get it to work. There might be a problem because they share an ip address. 
I've opened up the ports needed on my ubuntu desktop with the command 'sudo iptables -A INPUT -p tcp --dport 5900 -j ACCEPT'. Whenever I try to connect to my desktop it comes up with the error Host not found. The thing I'm using for the host is ouagadougou:0 (ouagadougou is my desktop's name).

Can anybody help?

---

### Post by dcstar on 2008-04-12
> **Christian Christiansen said:**
> I want to access my ubuntu 7.10 desktop from my windows 2000 laptop. I've got tightvnc and realvnc installed on both but I still can't get it to work. There might be a problem because they share an ip address. 
I've opened up the ports needed on my ubuntu desktop with the command 'sudo iptables -A INPUT -p tcp --dport 5900 -j ACCEPT'. Whenever I try to connect to my desktop it comes up with the error Host not found. The thing I'm using for the host is ouagadougou:0 (ouagadougou is my desktop's name).

Can anybody help?

What does " they share an ip address" actually mean?, if you want to connect from one machine to another then they need different IP addresses.

---

### Post by Christian Christiansen on 2008-04-13
When I go to a website which tells you your ip address (for example whatismyipaddress.com) on my laptop and desktop, the website says the ip addresses are the same. 

So do I have to change them, and if so, how?

---

