---
title: "w3m Can't load www.google.com, but Firefox can"
date: 2006-12-28
forum: General Help
---

### Post by topquark170 on 2006-12-28
Hi,

I've been using Ubuntu exclusively for four months now, and just decided to try doing everything in the command line (having come from windows).  I am currently running Ubuntu 6.10 on an Acer laptop, and am connected to the Internet over an Ethernet cable.

The problem:

$ w3m [http://www.google.com](http://www.google.com)
w3m: Can't load [http://www.google.com](http://www.google.com).

$ w3m [www.google.com](www.google.com)
w3m: Can't load [www.google.com](www.google.com).

I tried deleting ~/.w3m, but that hasn't fixed the problem.  I am able to load pages in Firefox and in Epiphany.   Does anybody have any suggestions as to what is going on, and, more importantly, how to fix it?

I think you will need more information, which I will be happy to provide.

Thank you in advance,

topquark170

---

### Post by dcstar on 2006-12-28
> **topquark170 said:**
> 
......
I tried deleting ~/.w3m, but that hasn't fixed the problem.  I am able to load pages in Firefox and in Epiphany.   Does anybody have any suggestions as to what is going on, and, more importantly, how to fix it?

I think you will need more information, which I will be happy to provide.

Thank you in advance,

topquark170

Do you have a Proxy setting for browsing?

---

### Post by topquark170 on 2006-12-28
> **dcstar said:**
> Do you have a Proxy setting for browsing?

Excellent!  I did, in fact, have Ubuntu set to connect to the Internet over my school's proxy server.  

Removing that and restarting the shell allowed w3m to connect.

Thank you so much!

[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
--topquark170

---

