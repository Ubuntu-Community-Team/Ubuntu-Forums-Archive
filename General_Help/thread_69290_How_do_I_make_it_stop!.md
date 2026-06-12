---
title: "How do I make it stop?!"
date: 2005-09-26
forum: General Help
---

### Post by AlexanRO on 2005-09-26
I downloaded and installed Azureus on both my Debian and Ubuntu machines, configured my Linksys router for port forwarding for both machines (as seen in screen shot).  On the Debian box when I perform a   "NAT /firewall test" I get the expected ouput: Testing port 6883 ... ok! However, when I perform the same on the Ubuntu machine I get: Testing port 6883 ... NAT Error, not to mention the occasional pop-up stating: if you have a router/firewall, please check that you have port 6883 UDP open. Decentralized tracking requires this.  Ports 6881-6999 have been forwarded (as seen in the screen shot).  I don't understand why it works on one but not the other.  Is IPtables/IPchains blocking access as well? How do I make it stop?!

---

### Post by yage on 2005-09-26
If you installed by apt it shouldnt do this. The firewall is activated by default in ubuntu. You can apt-get install firestarter to change things the easy way.

---

### Post by yyagol on 2005-09-26
[QUOTE=yage]If you installed by apt it shouldnt do this. The firewall is activated by default in ubuntu. You can apt-get install firestarter to change things the easy way.[/QUOTE]

it is the way to do it

---

### Post by Ken.Lank on 2005-09-26
I don't believe that you can forward the same port (or range) to 2 different IP addresses.  I'm guessing the PC with the top IP address is working, but not the bottom.

---

### Post by AlexanRO on 2005-09-26
[QUOTE=Ken.Lank]I don't believe that you can forward the same port (or range) to 2 different IP addresses.  I'm guessing the PC with the top IP address is working, but not the bottom.[/QUOTE]

I would have to agree with you on that one Ken.Lank disabling the second IP seems to have done the trick. Thanks to all of you for that advise.

Alexanro:smile:

---

