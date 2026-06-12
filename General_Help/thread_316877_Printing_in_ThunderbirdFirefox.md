---
title: "Printing in Thunderbird/Firefox"
date: 2006-12-11
forum: General Help
---

### Post by qseep on 2006-12-11
Hi folks,

When I print from OpenOffice, everything comes out fine. But when I print from Thunderbird/Firefox, the pages are scaled slightly too big to fit on the paper, so they get cut off on the left, right and bottom.

I'm using an HP LaserJet 2200d, with the HP LaserJet 2200 PostScript driver, connecting via JetDirect, resolution FastRes 1200.

Any ideas?

Thanks,
Lyle

---

### Post by altonbr on 2006-12-12
I THINK the answer is: go to _F_ile > Print Pre_v_iew > Page Set_u_p (or Page Pre_v_iew in Windows) and unselect "Shrink To Fit Page Width". If you WANT that on, then select it (or turn it on), of course.

---

### Post by qseep on 2006-12-21
Thanks, altonbr, but that didn't help. Any other ideas?

---

### Post by pseudo_nz on 2007-01-12
Firefox defaults to A4 size when it prints, so you'll need to set it to Letter (assuming you're in the US and using that size paper).

When you want to print, go to File - Print... and make sure you go into the Properties options next to the name of your printer and select the right sized paper.

---

### Post by tweedledee on 2007-01-13
> **pseudo_nz said:**
> Firefox defaults to A4 size when it prints, so you'll need to set it to Letter (assuming you're in the US and using that size paper).

When you want to print, go to File - Print... and make sure you go into the Properties options next to the name of your printer and select the right sized paper.

If papersize is the issue, you can change the system default in /etc/papersize (just change "a4" to "letter").

If that doesn't help, try printing to a pdf printer if you have it installed (cups-pdf) to see if it's the program or the printer's interpretation of the program's output that is causing the problem.

---

