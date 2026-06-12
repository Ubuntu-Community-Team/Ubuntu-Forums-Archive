---
title: "Could anyone explain proxy settings to me?"
date: 2007-03-31
forum: General Help
---

### Post by jasonal on 2007-03-31
I have to use http proxy to access Internet. In some apps like GAIM, if I set the proxy options of the gaim account to HTTP, there will be a connection error, saying or "Access denied: proxy server forbids port 1863 tunnelling" (for an MSN account). If I set the proxy options to NO PROXY or "Use global proxy settings", it works then, although in gnome configuration, /system/http_proxy/use_http_proxy is false and the environment variable http_proxy is also null.

Could anyone tell me how and where does gaim find the proxy settings? Thanks.

---

### Post by acormack on 2007-03-31
a proxy is a computer/device that accesses a service e.g. the internet instead (i.e. as a proxy) of your computer.

A common proxy is squid which ca be used as a web proxy accessing internet sites on behalf of clients which may no be able to access the net directly,

You only use a proxy if you have a proxy server on your network.

---

### Post by jasonal on 2007-03-31
Yes, there is a proxy server. And normally I have to configure the proxy setting manually. But how does GAIM so clever to find it?

---

### Post by acormack on 2007-03-31
What is the proxy server you are using?

How do you view its config?

from there you will find its settings which you key into your client.

normally for security reasons you have to know the settings to use.

---

### Post by jasonal on 2007-03-31
I'm not sure which proxy server it is. It is a http proxy server with port 3130. 
I get the config from internal network administrator.

---

### Post by acormack on 2007-04-01
I suspect the best answer is to talk to the network administrator

From what you are saying it sounds like there is a http proxy for web browsing but this is not configured to allow MSN to be proxied.

However since MSN works for you it would seem that you are allowed direct internet access for MSN without any proxy - this would be consistent with the results you are seeing.

I would definitely ask the network admin.

---

### Post by srinil on 2007-05-19
Hi,

  If your trying to communicate through proxy , you have to make sure that gaim port is enabled

---

### Post by airtonix on 2007-07-05
gaim port? 5222, 5223? 1863? or is it the other instant-messenger-protocols and the ports they use that you are referring to when you say "gaim ports"

---

