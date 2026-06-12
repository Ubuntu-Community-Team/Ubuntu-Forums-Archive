---
title: "ufw (or gufw ftm) basic settings"
date: 2013-02-16
forum: General Help
---

### Post by senca on 2013-02-16
Hey all,

wanted to use a simple firewall on my ubuntu machine and came across ufw. Installed gufw for the ease of it but I have a simple question. Does the firewall have basic settings already configured? The GUI shows me no rules at all so does that mean that the firewall just doesn't do anything?  Or are there some safety settings already applied when enabling ufw ?

greetings!

---

### Post by Bufeu on 2013-02-16
> **senca said:**
> Hey all,

wanted to use a simple firewall on my ubuntu machine and came across ufw. Installed gufw for the ease of it but I have a simple question. Does the firewall have basic settings already configured? The GUI shows me no rules at all so does that mean that the firewall just doesn't do anything?  **Or are there some safety settings already applied when enabling ufw ?**

greetings!
No.

---

### Post by mike555 on 2013-02-16
Using gufw turns on the builtin firewall on, it blocks incoming by default ......

---

### Post by Eglefino on 2013-03-06
Hi,

I have also a question about 'Gufw'. It was not installed standard, so I installed myself. I made all (open/close) ports from the listenreport and have read the log, which gave another askings to block some ports..... I cannot read on Ubuntu help-documentation if I made any faults or good corrections. Where can I read a better manual how all works?

---

### Post by black veils on 2013-03-06
i recently looked into what ports need to be enabled, here is what i gathered for my setup, although two may not be needed, they are for insecure email send/receive.

set incoming and outgoing to **deny**

then create rules to allow outgoing for:
udp 53,993,143
tcp 80,443,465,25,110,53,993,143

and using the preconfigured section for torrents, set to allow and out.

you can create these rules for more than one port at a time, and separate with a comma as shown above.

this list of port numbers may be useful to you [https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

### Post by mamamia88 on 2013-03-06
I really don't think you need gufw since ufw is uncomplicated enough as it is.  It's why it's called the uncomplicated firewall.  What I personally do is just do sudo ufw default deny and then sudo ufw allow port numbers i need.   Very simple and straight forward.

---

