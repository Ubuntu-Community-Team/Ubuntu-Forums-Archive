---
title: "How to use OpenDNS with a mixmaster postfix server?"
date: 2008-03-01
forum: General Help
---

### Post by miju on 2008-03-01
hi,

Can someone explain to me how to establish and integrate an OpenDNS service with a mixmaster/postfix server? I found a few tutorials for configuring postfix and mixmaster, but nothing to explain clearly how to do this along with a free DNS service.

---

### Post by stchman on 2008-03-01
> **miju said:**
> hi,

Can someone explain to me how to establish and integrate an OpenDNS service with a mixmaster/postfix server? I found a few tutorials for configuring postfix and mixmaster, but nothing to explain clearly how to do this along with a free DNS service.

I have a tutorial to get OpenDNS up and running with your router.

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

---

### Post by miju on 2008-03-01
> **stchman said:**
> I have a tutorial to get OpenDNS up and running with your router.

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

thank you, it seems helpful. But I have more than 1 computer behind my router and I want to continue to use my ISP to access the internet on some of them. 

Also I operate a Tor Onion server and a Freenet server, I would like to continue to rely on my ISP for bandwidth for these services. 

Can I configure the openDNS service to be used ONLY for the mixmaster/postfix server?:confused:

---

### Post by miju on 2008-03-01
*bump*

I really need a good explanation of this: can someone answer my prior post?:(

---

### Post by stchman on 2008-03-02
> **miju said:**
> thank you, it seems helpful. But I have more than 1 computer behind my router and I want to continue to use my ISP to access the internet on some of them. 

Also I operate a Tor Onion server and a Freenet server, I would like to continue to rely on my ISP for bandwidth for these services. 

Can I configure the openDNS service to be used ONLY for the mixmaster/postfix server?:confused:

You will still be using your ISP for your bandwidth, you will be using OpenDNS for name lookup.  If you enable OpenDNS at your router then all the PCs behind your router will use OpenDNS for name lookup.

---

### Post by miju on 2008-03-02
can I set the postfix and mixmaster programs to be the only ones to use openDNS? I have a d-link router which I can't find a setting to choose where to select how I do DNS lookups.:mad:

---

### Post by miju on 2008-03-02
*bump*

---

