---
title: "Unable to add printer"
date: 2015-06-15
forum: General Help
---

### Post by Camilia on 2015-06-15
Printer is connected via a USB. At 1st had option to add. Had to put in URI. I typed [http://localhost](http://localhost) 631. Now only have option to connect.  Does not connect. Get message There was an error during the CUPS operation: 'failed to connect to server'.

---

### Post by JKyleOKC on 2015-06-15
> **Camilia said:**
> Printer is connected via a USB. At 1st had option to add. Had to put in URI. I typed [COLOR="#FF0000"][http://localhost](http://localhost) 631[/COLOR]. Now only have option to connect.  Does not connect. Get message There was an error during the CUPS operation: 'failed to connect to server'.Try "http://localhost[COLOR="#FF0000"]_:_[/COLOR]631" instead. The colon is necessary, and spaces cause problems...

---

### Post by Camilia on 2015-06-15
> **JKyleOKC said:**
> Try "http://localhost[COLOR="#FF0000"]_:_[/COLOR]631" instead. The colon is necessary, and spaces cause problems...
Did that now printer is shown as connected but won't print. Would not even print the test.

When adding the printer clicked on HP3930 but it put in 3910
Printer state is Stopped - Rendering completed

---

### Post by Bucky Ball on 2015-06-16
Do you have HPLip installed? Presuming it's a HP. Install that from the Software Centre. You need to add the printer manually in cups, and that will include installing a driver for it. HPLip should provide that.

So, install HPLip from Software Centre> localhost:631> Add Printer (delete the other first)> choose the correct driver, it should appear when you get to that section but may not be where you expect so look through the whole list, when you get to that section. Good luck and let us know. :)

---

### Post by Camilia on 2015-06-16
> **Bucky Ball said:**
> Do you have HPLip installed? Presuming it's a HP. Install that from the Software Centre. You need to add the printer manually in cups, and that will include installing a driver for it. HPLip should provide that.

So, install HPLip from Software Centre> localhost:631> Add Printer (delete the other first)> choose the correct driver, it should appear when you get to that section but may not be where you expect so look through the whole list, when you get to that section. Good luck and let us know. :)
Yeh it is an HP. Found HPLIP tool box in the software center and downloaded it. Printed a test page. It is working. Thanks!!!\\:D/

---

### Post by Bucky Ball on 2015-06-16
That's what I like to hear. :)

When you have no doubt it is fixed, please mark this thread as solved (see second link in my signature). Good luck.

---

