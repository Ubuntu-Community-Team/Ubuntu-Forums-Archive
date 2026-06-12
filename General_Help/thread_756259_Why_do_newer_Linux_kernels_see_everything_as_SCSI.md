---
title: "Why do newer Linux kernels see everything as SCSI?"
date: 2008-04-15
forum: General Help
---

### Post by kahlil88 on 2008-04-15
When I first started using Linux, about three years ago, it labeled my hard drives as **/dev/hd****, but I've noticed that it labels them as **/dev/sd**** nowadays. Terminal commands like dmesg tell me I have SCSI drives, but isn't SCSI an interface, like Serial or Parallel ATA? It doesn't really make my life difficult or anything, but I'm a bit confused, and I don't think my drives suddenly evolved into something totally different overnight.

---

### Post by ibutho on 2008-04-15
The reason for the change is explained in detail on this [page]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce"). Look at the section that deals with PATA drivers.

---

### Post by tribaal on 2008-04-15
Interesting, I didn't know this was the reason :)

Thanks a lot!

- Trib'

---

