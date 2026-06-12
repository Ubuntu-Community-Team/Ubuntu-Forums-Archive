---
title: "What is port in computer?"
date: 2017-06-19
forum: General Help
---

### Post by linuxprj on 2017-06-19
hello,
I was reading an article there I found different port number what is this on the internet?

[https://qph.ec.quoracdn.net/main-qimg-2014194e8ef41a1e8c1de328d740ce9e](https://qph.ec.quoracdn.net/main-qimg-2014194e8ef41a1e8c1de328d740ce9e)

---

### Post by HermanAB on 2017-06-19
A Berkeley port isn't anything physical.  

A TCP/IP datagram contains a header which has the source address, destination address and port number (amongst other things).  This information is used by the computers to route the packets and figure out what to do with them.

For example, a SSH daemon listens on port 22, while a web server listens on port 80.  So if a computer receives a packet that is addressed to it, it can then use the port number to figure out which service should receive the packet for processing - the web server or the SSH daemon.

---

### Post by linuxprj on 2017-06-19
how computer convert website address to ip addr

---

### Post by Habitual on 2017-06-19
Server has a "phone number", ( aka the IP address).
Each Service is like a room in the house with a different extension.
Dial 1.2.3.4:80 you get the Kitchen/Web.
Dial 1.2.3.4:25 you get the Living Room/mail.

Have Fun.

---

### Post by SeijiSensei on 2017-06-19
> **linuxprj said:**
> how computer convert website address to ip addr

It's called the "Domain Name Service" or "DNS."  Think of it as an automated telephone directory.  You ask for [www.ubuntuforums.org](www.ubuntuforums.org) and the DNS server that is authoritative for that domain returns the following```

$ host www.ubuntuforums.org
www.ubuntuforums.org has address 91.189.94.16
www.ubuntuforums.org has address 91.189.94.12

```
There are two servers that answer to that name.  It's a method of providing load-balancing on busier sites like this one.

---

