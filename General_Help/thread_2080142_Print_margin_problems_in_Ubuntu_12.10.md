---
title: "Print margin problems in Ubuntu 12.10"
date: 2012-11-03
forum: General Help
---

### Post by am577 on 2012-11-03
Printer is HP 5515, paper size A4. Using the hpcups 3.12.6 driver, the printing is misaligned
at the top of the page; the margins are not set correctly. On earlier versions of Linux I was able to switch to the hpijs driver, and it worked correctly.
Now the hpijs driver doesn't work at all; it prints "Unable to open the initial device, quitting.".
Both these problems seem to have been around for some years, judging by queries on the net...
A solution to either problem would be welcome.
AM

---

### Post by pro1 on 2012-11-06
I've a similiar problem since Ubuntu 12.10 with a Brother HL-2240D laser printer. With Ubuntu 12.04 and a printer driver from Brother everything was fine, now with the same printer driver from Brother under Ubuntu 12.10 top and left margins are too wide so the page is cutted at the top and at the right edge. Really annoying. Has anyone found a solution?

---

### Post by supersoap on 2012-11-30
> **pro1 said:**
> I've a similiar problem since Ubuntu 12.10 with a Brother HL-2240D laser printer. With Ubuntu 12.04 and a printer driver from Brother everything was fine, now with the same printer driver from Brother under Ubuntu 12.10 top and left margins are too wide so the page is cutted at the top and at the right edge. Really annoying. Has anyone found a solution?

I'm having the same problem with my Brother HL-2270DW.

---

### Post by pro1 on 2012-12-30
Seems that the problem has something to do with CUPS 1.6 (Ubuntu 12.04 had CUPS 1.5) and the HL2240 PPD. Installing everything as usual (including Linux drivers from Brother website) and then changing the Printer driver to a Generic PCL5 seems to solve the problem (didnt measure margins with ruler, but it looks ok). So it looks like that the PPD provided by Brother isnt compatible with CUPS 1.6.

---

### Post by fiod3s on 2013-01-16
> **pro1 said:**
> Seems that the problem has something to do with CUPS 1.6 (Ubuntu 12.04 had CUPS 1.5) and the HL2240 PPD. Installing everything as usual (including Linux drivers from Brother website) and then changing the Printer driver to a Generic PCL5 seems to solve the problem (didnt measure margins with ruler, but it looks ok). So it looks like that the PPD provided by Brother isnt compatible with CUPS 1.6.

I'm experiencing the same problem with my Brother HL-2270DW. A workaround is to print to a .ps file then print from that file. However a better solution is to use a Generic PCL6 Driver.

---

