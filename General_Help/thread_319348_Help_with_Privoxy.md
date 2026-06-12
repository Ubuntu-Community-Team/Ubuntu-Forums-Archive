---
title: "Help with Privoxy"
date: 2006-12-15
forum: General Help
---

### Post by william_lee on 2006-12-15
I've recently installed privoxy successfully under Edgy.   It is working fine on the box that it is installed on, but I am having trouble accessing the proxy from other PCs on the network.

I have edited the privoxy config file to listen on :8118 which if I understand the documentation correctly should allow connections from anywhere.

I have tried putting in both the the local IP of the privoxy box and the internet IP, and port 8118 into my browser proxy config on another PC.

After doing this, I am unable to connect to any websites on that PC.

Any ideas?  I couldn't find anything else in the docs or on google that helped.

Thanks!

---

### Post by dcstar on 2006-12-15
> **william_lee said:**
> I've recently installed privoxy successfully under Edgy.   It is working fine on the box that it is installed on, but I am having trouble accessing the proxy from other PCs on the network.

I have edited the privoxy config file to listen on :8118 which if I understand the documentation correctly should allow connections from anywhere.

I have tried putting in both the the local IP of the privoxy box and the internet IP, and port 8118 into my browser proxy config on another PC.

After doing this, I am unable to connect to any websites on that PC.

Any ideas?  I couldn't find anything else in the docs or on google that helped.

Thanks!

You may first want to check the network connectivity into the proxy by opening a command box on another PC and:
```
telnet whatever-proxy-ip-is 8118
```
Then if you type something (anything!) you should get some sort of response from the Proxy server (if you can connect to it).

If you cannot even connect to the port, then you have some networking/port blocking issues, if you can but still cannot get to websites, then you probably have a configuration issue in the proxy.

---

