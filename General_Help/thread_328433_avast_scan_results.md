---
title: "avast scan results"
date: 2006-12-30
forum: General Help
---

### Post by DougieFresh4U on 2006-12-30
Just for thethrill of it,I installed avast antivirus.I ran a complete scan and in the screen shot here you will see some problems. There is a lot more not shown. What & how do I deal with them. And if possible can some one explain what some of them mean. :confused:   Thanks.

---

### Post by snowx1000 on 2006-12-30
The scan is giving those errors because it is essentially trying to scan hardware. On top of that the hardware may not even exist. In linux hardware appears as files such as a cdrom being /dev/cdrom. You should usually only scan your home directory (most viruses do not affect linux anyway). The only scanning I would really suggest for the root partition is rootkithunter available from ([http://rkhunter.sourceforge.net/)](http://rkhunter.sourceforge.net/)). You would not really need this either unless you are installing a lot of untrusted packages.

---

