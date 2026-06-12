---
title: "Tor/Privoxy across a LAN"
date: 2005-08-14
forum: General Help
---

### Post by Hikaru79 on 2005-08-14
Okay, I have a LAN of Linux (mostly Ubuntu) machines. One of them acts as a dedicated file/web/print server. Now, I've succesfully used Tor by installing it on each machine in the LAN and just running it on 'localhost', but I'd like to have it going on that one server, and have every machine in the LAN go through it for their Tor fix. The local IP of the server is 192.168.1.23 and lets say that the client I'm interested in has a local address of 192.168.1.15 . I installed it and read through the privoxy conf file. I changed the line```
listen-address 192.168.0.1:8118
``` to ```
listen-address 192.168.1.23:8118
```, and now I have no problems connecting to the proxy from my client. However, although it is going through the proxy, its not doing any anonymizing. [www.whatismyip.com]("http://www.whatismyip.com") still gives me my old original address. What am I missing?

Here's the forward-socks4a lines I have tried, in various combinations:```
forward-socks4a / localhost 9050 .
forward-socks4a / 192.168.1.15 9050 .
forward-socks4a / 192.168.1.23 9050 .
```

Thanks in advance! :)

---

### Post by Hikaru79 on 2005-08-15
Sorry to bump, but ... anyone? :?

---

