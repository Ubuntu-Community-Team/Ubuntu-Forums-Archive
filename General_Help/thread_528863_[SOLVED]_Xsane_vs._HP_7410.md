---
title: "[SOLVED] Xsane vs. HP 7410"
date: 2007-08-18
forum: General Help
---

### Post by rtrdom on 2007-08-18
Using Feisty, the Hp7410 prints fine over wireless network. Same machine, same
Feisty, and Xsane says "no devices available". Have upgraded to v. 2.7.7 driver for scanner.
Still cannot see. In terminal, lsusb does not show scanner or printer, anywhere.
  Scanner works well with other OS. Any ideas how to make Xsane see the scanner?

---

### Post by gobbles414 on 2007-08-19
Hi rtrdom,

This is a question of ignorance on my part: does the sane backend support wireless network scanning. I have had a lot of trouble just getting USB all-in-ones working with the sane backend. So it seems to me that it is unlikely that sane offers wireless printing support. Can you confirm...?

---

### Post by rtrdom on 2007-08-26
The printer portion of the HP7410 was working fine via wireless from a Presario
X1000. However, after upgrading to hplip v 2.7.7 the printer does not print, the
scanner does not scan. The lsusb output says not there. lstat-t shows the printer
to be present via wireless network, says it is printing but the printer does 
nothing. Spent about 4 hours today (8/26/2007) trying to make it print but so
far nothing good. It has to be something in the xsane software because the
printer and scanner and fax work well with XP.  Any help appreciated.

The printer is now printing (8/27/2008) 0002hrs. Found infor at [http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)
and followed all manual directions. Printed test page perfectly and quickly.

When I ran code hp-check there was a warning:" Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP"

Now, if I can get scanner to work I'll be happy. (ier)

Scanner works.

I consider this problem solved.

THE SCANNER WORKS! I did nothing else.  For installation of HP 7410 full operation under Feisty, the link above will provide
the information.

Now Scanner does not work due to changing IP address in router.  Need to change IP address in Xsane but cannot find it.  See entry dated 9/9/2007.

---

