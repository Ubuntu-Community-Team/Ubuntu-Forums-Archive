---
title: "Kernel 2.6.15-26-686 and Atheros"
date: 2006-07-20
forum: General Help
---

### Post by ajack on 2006-07-20
Hi all,

I have an Acer 3624 and have been happily using Dapper since it was in beta.  I just upgraded to the later kernel (2.6.15-26-686) and after this upgrade, I am unable to use my wireless network connector.  Doing an lspci I get:

```

0000:06:05.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

```

using dmesg, I get the following:

```

[17179592.552000] ath_pci: Unknown symbol ath_hal_getwirelessmodes

```

And before this, I was happily using my Atheros wireless without problems.

Anybody can help me with this?  I really need my wireless...  ](*,)

---

### Post by Ramses de Norre on 2006-07-20
Do you have the restricted modules for your kernel installed? I have an atheros too and it works fine here..

---

