---
title: "apt-get still referring to proxy information"
date: 2007-05-14
forum: General Help
---

### Post by mskadu on 2007-05-14
Hi everyone,

I installed 7.04 when inside a network proxy. During the installation, it prompted me for proxy info and things were ok.

Now, I have moved out of outside the proxied network. I changed the details in System Preferences > Network Proxy.

Now, when i do a "sudo apt-get update", i can still see apt-get trying to connect via the proxy. Any idea, what else I need to change?

thanks in advance..

======================

This has been sorted now. The proxy settings remained in /etc/apt/apt.conf, Though I am not sure why they did. Renaming the file did the trick :popcorn:

---

### Post by bapoumba on 2007-05-14
Oooops, sorted out !

---

