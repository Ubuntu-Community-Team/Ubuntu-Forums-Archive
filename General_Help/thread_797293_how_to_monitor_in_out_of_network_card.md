---
title: "how to monitor in out of network card"
date: 2008-05-17
forum: General Help
---

### Post by taimur on 2008-05-17
hi
how to monitor in and out of network card mean eth0 in command line?

---

### Post by dcstar on 2008-05-17
> **taimur said:**
> hi
how to monitor in and out of network card mean eth0 in command line?

Monitor what?, traffic peaks?, packet contents?

---

### Post by taimur on 2008-05-17
every thing

---

### Post by Monicker on 2008-05-17
You can use tcpdump or wireshark to monitor and capture all of the actual packets.  If you are just concerned about the number of packets, you can use a tool like bmon.

---

### Post by 9x0 on 2008-05-17
> **taimur said:**
> hi
how to monitor in and out of network card mean eth0 in command line?

Try *iftop*. It's quite nice and it will probably suit your needs.

---

