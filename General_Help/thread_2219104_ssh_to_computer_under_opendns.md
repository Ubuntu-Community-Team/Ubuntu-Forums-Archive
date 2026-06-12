---
title: "ssh to computer under opendns"
date: 2014-04-22
forum: General Help
---

### Post by lance bermudez on 2014-04-22
How can I ssh from work to a computer in my home network. dyndns-free.com is working for me but I want to try out opendns.com. 
ssh -p # [email]user@domainlable.dyndns-free.com[/email]

How do I do that for opendns?

---

### Post by dragonfly41 on 2014-04-23
Not really answering your question about opendns ..

but does this interest you for secure tunneling .. [https://ngrok.com/](https://ngrok.com/)

---

### Post by CaptainMark on 2014-04-23
Are you asking how to setup opendns or how to connect to a computer on your home network? Your post isn't very clear.

Once you have your home computer acting as an SSH server and properly configured either your router or the computer to update your dynamic dns then you just connect using a similar command to what you just typed.

ssh [user]@[domain] -p [port]

so whatever domain name you've got from opendns you place instead of [domain] here

---

### Post by lance bermudez on 2014-04-25
thank you all for your help but I got an email form opendns and they say that they do not support remote connections that I need a dynmic dns.

---

### Post by cmcanulty on 2014-04-25
try no-ip.com for a free dyndns service there are numerous others
[http://www.gnutomorrow.com/best-free-dynamic-dns-services-in-2013/]("http://www.gnutomorrow.com/best-free-dynamic-dns-services-in-2013/")

---

