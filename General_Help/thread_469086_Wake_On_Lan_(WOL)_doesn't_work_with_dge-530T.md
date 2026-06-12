---
title: "Wake On Lan (WOL) doesn't work with dge-530T"
date: 2007-06-09
forum: General Help
---

### Post by carloshss on 2007-06-09
Hi.

I'm trying to use wol with a [[COLOR="RoyalBlue"][COLOR="Orange"]d-link dge-530T[/COLOR][/COLOR]]("http://www.dlink.com/products/resource.asp?pid=284&rid=879&sec=0"), but no success until this moment.
My BIOS and NIC supports this feature. I already used the scenarios below:

- wol with an older NIC and windowsXP: works
- wol with an older NIC and [COLOR="DarkOrange"]Ubuntu*[/COLOR]: works
- wol with dge-530T and windowsXP: works
- wol with dge-530T and [COLOR="DarkOrange"]Ubuntu*[/COLOR]: doesn't work :(
- wol with dge-530T and [COLOR="Sienna"]Ubuntu**[/COLOR]: doesn't work :(

Could it be a driver issue?

Additional info:

Motherboard: Intel D865Perl

[COLOR="DarkOrange"]Ubuntu*[/COLOR]
version: Ubuntu 6.06.1
kernel: 2.6.15-28-686
nic driver: sk98lin 8.23.1.3 (01)

[COLOR="Sienna"]Ubuntu**[/COLOR]
version: Ubuntu 7.04
kernel: 2.6.20-16-generic
nic driver: skge version 1.9

Thanks for helping.
Carlos

---

### Post by carloshss on 2007-06-14
Hi everyone!

I solved this problem updating my kernel (version 2.6.21). This kernel version has a skge 1.10 driver that works fine in this case.

Regards
Carlos

---

### Post by gaberhakim76 on 2007-10-23
Hi Carlos
Please Tell Me What You Did To Get Your Wake On Lan Feature Working, I Got The  Same Card And My Motherboard Does Support The Won Feature.
However, I Don't Know Where It The Won Cable Connector On The Nic..
Please Help
Thanks Alot
Gaber

---

### Post by carloshss on 2007-10-24
Hi Gaber.
I'll post my answer here to complete the thread.

[QUOTE=carloshss]Hello.

To solve this problem I upgraded my Ubuntu version to 7.10 and everything worked fine for me.
Another solution is to use a higher kernel version like 2.6.21.
I follwed a tip on this site [http://n3rd3x.blogspot.com/2007/05/instalando-kernel-2621-em-seu-ubuntu-d.html]("http://n3rd3x.blogspot.com/2007/05/instalando-kernel-2621-em-seu-ubuntu-d.html")
This page is in Portuguese, but I think you can follow the steps (etapas).

This cable (also called WOL cable) is for older NICs.
I think this cable is present for compatibility issues. It means if you buy (or already have) a older card that provides wol feature, it probally will work with your motherboard.
For more informatiom, see this page [http://www.intel.com/support/network/sb/CS-000084.htm]("http://www.intel.com/support/network/sb/CS-000084.htm")

Hope it can help you

Carlos[/QUOTE]

---

