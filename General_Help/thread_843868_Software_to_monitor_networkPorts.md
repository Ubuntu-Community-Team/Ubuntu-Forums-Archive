---
title: "Software to monitor network/Ports"
date: 2008-06-28
forum: General Help
---

### Post by bzachd on 2008-06-28
Hi,

Looking for some info on Software. Wondering what product to use to monitor my Network. I have a wireless network with my Ubuntu box tied in directly to my Router. I have an Oracle 11G database running, which is accessible through my router port forwarding through port 80. Everything thing works great, and Ubuntu runs Oracle like a champ... but I wanted to keep an eye on network traffic through port 80 to my Ubuntu box. Something that just logs connections through port 80. Any advice would be appreciated.

Thanks!
Zach

---

### Post by pdwerryhouse on 2008-06-28
You can manually monitor the port with tcpdump, but if you'd prefer something that can just sit in the background and monitor based on rules that you define, you might want to look at snort (which is in the ubuntu repository).

---

