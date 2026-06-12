---
title: "OpenDNS causes Printing to XP box failure"
date: 2007-12-03
forum: General Help
---

### Post by Boelcke on 2007-12-03
OK, I have an odd one.

I have Ubuntu 7.10 freshly installed on a laptop. I have a Brother HL-2040 attached to a desktop running WinXP.  When I tried installing a printer, it worked beautifully.

System, Administration, Printing
Windows Printer via SAMBA (already had SAMBA installed through Synaptic)
Browsing through the network found the shared printer.
Sweet.

Now, I switched from using my ISP's DNS servers to OpenDNS.  I set this in the router only. Suddenly, printing from the Ubuntu laptop stops working.  Print Test Page yields nothing.

I ended up going into Ubuntu's Network settings, (System, Administration, Network), and entered both my ISP's DNS servers, and OpenDNS's.  When my ISP's are at the top of the list, it worked fine.  When OpenDNS's are at the top of the list, no printing.  Any ideas?

Some reading seems to indicate that switching the DNS servers over to something else, such as OpenDNS, messes up Samba.  I'm just not real sure how to fix it!

---

