---
title: "SSH login through Proxy"
date: 2006-09-11
forum: General Help
---

### Post by Elrohir on 2006-09-11
been looking around and no thread that may help me has been found...

I have a SSH Server at home, but in my office I have Internet through a proxy and I want to login to my server... thing is that I have to login to proxy so I can get out...

how can I login to proxy?

System > Preferences > Network Proxy is already configured to point to the proxy, and in Details is filled with the login info... no luck... any ideas?

---

### Post by Lunar_Lamp on 2006-09-11
You will need to set the proxy options in your ~/.bashrc

I cannot remember the format for specifying your username and password, so you will need to google for it, but my (no-login) proxy details are provided by this line:

 export http_proxy="PROXY-URL:PORTNUMBER/"

I think it may be:

 export http_proxy="USER@PASS:PROXY-URL:PORTNUMBER/"

I don't know if you can use ssh through a proxy, but I don't see why not.

---

### Post by Lunar_Lamp on 2006-09-11
Just found this link which may help.  I wish I had found it earlier myself!

[http://www.mtu.net/~engstrom/ssh-proxy.php](http://www.mtu.net/~engstrom/ssh-proxy.php)

---

