---
title: "Why do I need a proxy server? Is SQUID easy to configure?"
date: 2007-12-26
forum: General Help
---

### Post by kevdog on 2007-12-26
Maybe this is an easy question.   Im using ssh tunneling for remote internet access from coffee shops, work, etc to provide some form of encrypted communication.  Ive seen sight talk about doing this (its actually very easy), but some recommend use of a proxy server of the sshd machine.  I understand proxy server do website caching, do I really need this feature?  Also if the ubuntu forums website is cached in the proxy server, are the pages regularly updated?

Finally is SQUID really easy to setup?  I guess this is a loaded question depending on how complex you want to make squid.

---

### Post by daleus on 2007-12-26
If you are connecting from a Mac or Linux machine try put this

ssh -D 7070 username@server

or if you run ssh on a non-standard port

ssh -p 443 -D 7070 username@server

This creates a LOCAL socks 5 proxy (effectively) through the tunnel, just set your browser (or whatever) to use socks 5 proxy 127.0.0.1:7070

No need for squid.


If connecting from windows, using putty, go to Tunnels and select "Dynamic" and type in 7070.

This means you don't need squid, however the only time I set up squid was on PcLinuxOS and it was dead easy, so I imagine ubuntu should be just as nice.

---

### Post by kevdog on 2007-12-27
Thanks for the dynamic socks addition -- that is great info.  Squid -- maybe Im going to give up on that option for now. I would be nice if with the web pages that are cached, it would automatically go out and look for page changes every so often.

---

