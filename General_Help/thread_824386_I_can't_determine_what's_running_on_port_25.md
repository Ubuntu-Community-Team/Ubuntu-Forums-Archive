---
title: "I can't determine what's running on port 25?"
date: 2008-06-10
forum: General Help
---

### Post by alzamabar on 2008-06-10
Hi, I want to run a server of mine on port 25 (I'm writing an SMTP server). However when I start it it says that it cannot connect to port 25 because of Permission Denied. 

I typed telnet localhost 25 and I got the following:

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 jemoslinux ESMTP Sendmail 8.14.2/8.14.2/Debian-2build1; Tue, 10 Jun 2008 07:03:13 +0100; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]

Do you know what's running and how can I stop/uninstall it?

I tried to check sendmail and ESMTP on the Synaptic Package Manager but nothing showed up as installed.

Thanks.

M.

---

### Post by iaculallad on 2008-06-10
Try running **netstat -natp** in your terminal if it gives the data you needed.

---

### Post by cariboo on 2008-06-10
Telnet acces is turned off by default. To find out what ports are open, use nmap. There is a gui for namp too. they are located in the repositories. To make it easy:

```
sudo apt-get install nmap nmapfe
```

Jim

---

