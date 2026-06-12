---
title: "Printing problem (rendering completed)"
date: 2015-06-15
forum: General Help
---

### Post by andfree on 2015-06-15
Hi. I connected a HP Deskjet Ink Advantage 1515 All-in-one Printer on USB port and installed the recommended driver (not the exact model number for the specific printer). I printed some pages without problem or, to be accurate, with some problems with missing text at margins which I tried to fix. But after some pages printed, it stopped printing and got a "rendering completed" message. I tried reinstall the recommended driver, but it never printed a page again. I searched for a ppd file, but I don't find one. Laptop is on Ubuntu 12.04. Any idea that could help me? Thanks.

---

### Post by ajgreeny on 2015-06-15
And the driver you used?
Difficult to help without knowing more.

---

### Post by andfree on 2015-06-15
hpcups 3.12.2[en] for Deskjet 1280. It was the recommended one.

I would try to provide a ppd file for the exact model (HP Deskjet Ink Advantage 1515 All-in-one Printer), but I can't find one.

---

### Post by andfree on 2015-06-15
I also tried the installed hplip using the command hp-setup without success; it didn't print. I also installed the latest version using the automatic installer (hplip-3.15.6.run). And the minimum version 3.13.8. Nothing worked.

---

### Post by andfree on 2015-06-16
After upgrading to 14.04.2, the printer works. I don't know if I should mark the thread as "solved".

The margins issue remains. A line of text is cut-off at the bottom of the page. Is there a simple solution or I should start a new thread about this?

---

### Post by Bucky Ball on 2015-06-16
The driver you installed was recommended by whom? You install HPLip from the Software Centre, not from the HP Linux site. That way it will install without issue. ALWAYS check the official repos first. You can save yourself some time and headache. You may be reinventing the wheel ...

If you are using the driver for a different printer, it probably accounts for your margin issue. You need to install the correct driver. 

Uninstall whatever printer you have installed. Install HPLip from the Software Centre or Synaptics or a terminal> Open a browser> type 'localhost:631' in the address bar to open the cups interface> Add printer> find the correct driver when you get to the install driver part.

If you cannot find the exact driver for your printer, go back, you are going the wrong way.

---

