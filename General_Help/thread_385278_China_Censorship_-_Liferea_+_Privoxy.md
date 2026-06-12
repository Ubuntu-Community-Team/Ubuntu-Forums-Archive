---
title: "China Censorship - Liferea + Privoxy"
date: 2007-03-15
forum: General Help
---

### Post by cisforcojo on 2007-03-15
Hey guys,

Does anyone know how to use privoxy with liferea? I get Tor + Privoxy working great in firefox but no idea how to get it working in Liferea. It's really annoying. RSS feeds like Hack the Planet aren't avialable to me. THAT one I can see them blocking but other sites like Automatix are also banned. Who knows why. Anyway, any help would be greatly appreciated!

---

### Post by peabody on 2007-03-15
Found this, not sure if it helps:

[http://trac.feedtree.net/project/wiki/ProxySetup/Liferea?format=txt](http://trac.feedtree.net/project/wiki/ProxySetup/Liferea?format=txt)

---

### Post by cisforcojo on 2007-03-15
Nah I knew where to put the proxy settings. Thanks for your help I'll research it a little more.
I know in firefox you set the proxy server to localhost, port 8118

---

### Post by cisforcojo on 2007-03-16
Alright I see in Liferea that there's a PROXY option but it says that it uses the default GNOME proxy options. I don't want my entire internet to be proxied, just Liferea. Anyone know how to set this up?
I haven't had any luck finding a good anonymous proxy server from [www.proxyblind.org](www.proxyblind.org) either. Any advice there? It needs to have a high anonymity level in order to get around the blocking.

---

### Post by zanglang on 2007-03-17
Hmm... one way you could do it is open up a console, type in "export http_proxy=<address>:<port>", and then start liferea from the console. Or make a startup script that does combines both, e.g. liferea.sh, containing "http_proxy=xyz:3128 liferea". There's probably some other way around this though.

---

