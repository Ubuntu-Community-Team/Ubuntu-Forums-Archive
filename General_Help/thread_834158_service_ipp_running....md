---
title: "service ipp running..."
date: 2008-06-19
forum: General Help
---

### Post by gkjau on 2008-06-19
I decided to scan my pc with nmap and nessus and it showed a service running on port 631, ipp. Nessus showed it as a webserver, but i dont have it on my pc....i've just installed ubuntu a week ago....
What should i do to stop this service??
thx

---

### Post by polki@mac.com on 2008-06-19
I think it's CUPS running. Your friendly neighbourhood Common Unix Printing System.

---

### Post by bodhi.zazen on 2008-06-19
cups == port 631

ipp == Internet printing protocol (netwroked printer).

[http://en.wikipedia.org/wiki/Internet_Printing_Protocol](http://en.wikipedia.org/wiki/Internet_Printing_Protocol)

If you have a network printer you are fine. If not, shut down CUPS (you will not be able to print if you shut down cups). Of course you can leave cups off and turn it on / off only when you print ...

---

