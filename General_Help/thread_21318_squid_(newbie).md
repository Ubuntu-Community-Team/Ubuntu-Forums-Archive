---
title: "squid (newbie)"
date: 2005-03-21
forum: General Help
---

### Post by jmckendrick on 2005-03-21
I want to use a machine with ubuntu as a proxy server in a Windows 98 network. How do I set it up? I believe I need to use Squid - and that is about as much as I know! Thanks for any help.

---

### Post by tonym on 2005-03-23
I haven't done this on Ubuntu but its quite easy on Debian so I expect Ubuntu to be the same.

First just install the squid package.  There is a default config file.  The only changes I've made are:

Specify port to use:

```
http_port  80
```

Create my own acl for my local network

```
acl localnet src 192.168.0.0/255.255.0.0
```

Give access to my network

```
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
# And finally deny all other access to this proxy
http_access allow localnet
http_access deny all
```

Then just configure your Windows clients to point to port 80 on your server.

Regards

Tony Middleton

---

