---
title: "SMTP server on my desktop?"
date: 2007-11-20
forum: General Help
---

### Post by mafsi on 2007-11-20
Hi,

I need some help to configure a SMTP server for mai T-Bird Client in order to send emails.
As you know in Account Settings you need to put a SMTP server but i don't wat to use smtp.gmail.com

I want to put there: localhost and port 25 to send mails direcly from my Desktop Ubuntu 7.10
I have to tell you that my ISP is giving me a new IP every time i connect to the internet & although is giving me a smtp to send email, this is limited to 5 MB attach

Can you help me to achive this?
Thanks in advanced.:)

---

### Post by posterboy on 2007-11-20
I'm doing this, and have been for years. At the moment, I am using postfix as my MTA, there's a fairly steep learning curve to running your own mail server, but, postfix may be one the easiest ones. You will also need a domain name, and a DNS provider that automatically resolves your current IP to your domain name. There are several of these, dyndns comes to mind. Open port 25, and watch the mail roll in. Be aware that while your ISP handles spam prevention, it now becomes YOUR responsibility, and that's another learning curve. Worth it, though, I have enjoyed the experience a lot.

---

### Post by mafsi on 2007-11-20
> **posterboy said:**
> I'm doing this, and have been for years. At the moment, I am using postfix as my MTA, there's a fairly steep learning curve to running your own mail server, but, postfix may be one the easiest ones. You will also need a domain name, and a DNS provider that automatically resolves your current IP to your domain name. There are several of these, dyndns comes to mind. Open port 25, and watch the mail roll in. Be aware that while your ISP handles spam prevention, it now becomes YOUR responsibility, and that's another learning curve. Worth it, though, I have enjoyed the experience a lot.

here is what i did:

```
sudo apt-get install postfix

edited  /etc/postfix/main.cf & i replaced

inet_interfaces = all

with

inet_interfaces = 127.0.0.1

then

sudo /etc/init.d/postfix restart
```

is not about sending spams but Google already know about us a lot & i dont want to give it more :))

---

### Post by posterboy on 2007-11-20
Also, another cautionary tale, a must read, google for backscatter. You don't want to contribute to this problem, for sure.

---

