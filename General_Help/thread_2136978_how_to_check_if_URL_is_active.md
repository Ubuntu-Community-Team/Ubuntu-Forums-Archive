---
title: "how to check if URL is active ?"
date: 2013-04-19
forum: General Help
---

### Post by winzip on 2013-04-19
I have a web service url .  service is hosted in a remote box.

I want to check if  web service is running or not.

what is the command to shoot to check if  web service is up or down ?

---

### Post by vasa1 on 2013-04-19
Will [http://www.isup.me/](http://www.isup.me/) help?

---

### Post by HermanAB on 2013-04-19
Here are a few:
telnet ipaddress 80
nc ipaddress -p 80 (or ncat, socat...)

Or check via a proxy service such as google translate.

Another way to confirm that something is reachable from around the world is with a Tor bowser, since each time you start Tor up, you are assigned a different exit node.

---

### Post by tgalati4 on 2013-04-19
```
man curl
```  There are quite a few switches that you can use to measure web server performance.

---

### Post by winzip on 2013-04-20
> **HermanAB said:**
> Here are a few:
telnet ipaddress 80
nc ipaddress -p 80 (or ncat, socat...)


There is no internet.

However web service is in LAN.

Also, telnet won't  tell whether service is deployed and up properly.....yes..it can tell whether server is running in that port correctly.

no browsing ...as there is no internet

---

### Post by winzip on 2013-04-20
> **tgalati4 said:**
> ```
man curl
```  There are quite a few switches that you can use to measure web server performance.

I know the service end point URL.

Can you please tell how curl can help me to check if the service is up and running ?

---

### Post by CharlesA on 2013-04-20
> **winzip said:**
> There is no internet.

However web service is in LAN.

Also, telnet won't  tell whether service is deployed and up properly.....yes..it can tell whether server is running in that port correctly.


If the web server is listening for incoming connections, it usually means it's running and configured correctly. Either check to see if that port is open with something like nc or telnet, or just browse to the site being hosted there to verify it is up and running.

---

### Post by winzip on 2013-04-20
> **CharlesA said:**
> If the web server is listening for incoming connections, it usually means it's running and configured correctly. 

No. for example, say the server has hosted 3 service in same 8080 port (it can be done)....your telnet to IP Adress and port is not sufficient to tell whether service 2 is running or not.....it will tell wehther port 8080 is connected or not though.

There is no GUI in the box. service is hosted in LAN....not in www.

I am connecting through putty.

---

### Post by CharlesA on 2013-04-20
If you are hosting multiple sites on the same machine, you will usually be using virtual hosts, so you would need to access those sites via their URL.

---

