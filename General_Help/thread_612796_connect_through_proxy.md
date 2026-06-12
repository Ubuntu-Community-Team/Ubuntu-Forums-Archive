---
title: "connect through proxy"
date: 2007-11-14
forum: General Help
---

### Post by matt91 on 2007-11-14
I have a server with ubuntu server 7.10 installed. To access the internet it must go though a proxy. I have searched on the internet but could not find where to put the proxy info. does anybody know how to do this?

Thanks, Matt.

---

### Post by bingoUV on 2007-11-14
> **matt91 said:**
> I have a server with ubuntu server 7.10 installed. To access the internet it must go though a proxy. I have searched on the internet but could not find where to put the proxy info. does anybody know how to do this?

Thanks, Matt.

Since it is a server install I am assuming you do not seek to browse the internet using the usual browsers like firefox. You want to run a server / application which needs to connect to the internet. Which server / application is it? 

Many applications will honour the environment variable http_proxy (assuming it wants to connect using http). If your http proxy server is matt91 and port is 80, set the environment variable thus
```

export http_proxy=matt91:80

```

---

### Post by matt91 on 2007-11-14
I just need apt and wget to work, i think i have found how to get apt to work by putting Acquire::http::Proxy "http://proxy.example.com:3128";; in the apt.conf file and using -proxy=on with wget. I will test tommorow when i can access the server

---

