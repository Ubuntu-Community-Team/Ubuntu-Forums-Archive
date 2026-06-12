---
title: "Dns problem?.. Please help"
date: 2018-02-15
forum: General Help
---

### Post by sternfanatic on 2018-02-15
Hello: I am new to ubuntu. I have an Ubuntu LTS 16.04 setup with apache. I have 3 domains. They are pointed to my Public IP address and I use namecheap dns service as I am on a dynamic IP address. When I attempt to contact any of my 3 domains, I cannot connect to them. I get ERR_CONNECTION_TIMED_OUT I have set up port forwarding on port 80 to my Ubuntu machine IP 10.0.0.111 If I type 10.0.0.111 from my windows 10 computer I can see my index.html page. But only my one website, not the other two. 
When I do a nslookup on my domains, it resolves to my public IP. 

What am I doing wrong? I have been searching for help for weeks.

---

### Post by dragonfly41 on 2018-02-16
I'm assuming that you are trying to expose a localhost home server (port 80) to the web?

I will venture a few ideas ...

(a) Have you properly setup list of multiple hosts in /etc/hosts file?

(b) Have you checked your ISP policy re: serving content from localhost server? They might be blocking port 80. 

(c) If you are setting up a local home server to demonstrate some content then you might find ngrok is useful .. [https://ngrok.com/](https://ngrok.com/)
     You will then need to setup /etc/hosts and your namecheap service to point to the ngrok allocated url's.
     Here is one article explaining setup multiple sites in YAML file ... [https://helgesverre.com/blog/expose-local-webserver/](https://helgesverre.com/blog/expose-local-webserver/)
     
     And another ...
     [https://blog.rodneyrehm.de/archives/38-You-may-not-need-localtunnel-or-ngrok.html](https://blog.rodneyrehm.de/archives/38-You-may-not-need-localtunnel-or-ngrok.html)

---

