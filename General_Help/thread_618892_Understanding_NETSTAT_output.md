---
title: "Understanding NETSTAT output"
date: 2007-11-20
forum: General Help
---

### Post by Blue Sassley on 2007-11-20
I have a server that I am running a couple of different domains on it and I wanted to know how I know which domains the remote connections are going to with the NETSTAT command... right now I just get output showing the main domain and not the others that are being hosted.

Thanks for the help,
Blue

---

### Post by mannih2001 on 2007-11-22
What you are trying to achieve is impossible, I guess. netstat is dealing with IP addresses and it will translate those to hostnames. But there can be only one hostname per IP-address. 

You would have to sniff your traffic and pick out the http Host-headers to get the information you want.

---

