---
title: "Booting through Putty"
date: 2007-07-16
forum: General Help
---

### Post by sdmike on 2007-07-16
So I mostly use my linux box through putty because awhile back my kvm switch died and I got used to it this way. 

What I want to know is, is it possible for me to turn on my pc through putty?

---

### Post by splintercellguy on 2007-07-16
Don't think so. On a side note, however, I've seen those KVM devices with a VNC server on them that hook up to your comp's PS/2/video ports.

---

### Post by Peter76 on 2007-07-16
you could use wake on lan

---

### Post by sdmike on 2007-07-16
I think it has a wake on lan in the bios. 

But how would that work because I quite don't get it?

If I try to Putty to it does the machine boot up?

---

### Post by splintercellguy on 2007-07-16
PuTTY wouldn't work at all, since there's nothing running that could accept the connection, let alone handle SSH. I guess maybe VPN into the network and send the magic packets?

---

### Post by sdmike on 2007-07-16
So I read up on Wikipedia about waking up on LAN. I saw how to configure Linux to wake up on LAN.

But I'm not really getting how to send the Magic Packet to make the system boot.

All I know is how to send it to either port 7 or 9.

Because once the computer starts I can SSH into it.

So how do I send a Magic Packet?

---

### Post by sdmike on 2007-07-16
Bump!

---

### Post by splintercellguy on 2007-07-16
[http://en.wikipedia.org/wiki/Wake_on_LAN#Wake-on-LAN_programs](http://en.wikipedia.org/wiki/Wake_on_LAN#Wake-on-LAN_programs)

Ton of apps.

---

