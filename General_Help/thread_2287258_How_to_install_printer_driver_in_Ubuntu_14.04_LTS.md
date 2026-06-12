---
title: "How to install printer driver in Ubuntu 14.04 LTS?"
date: 2015-07-18
forum: General Help
---

### Post by Rajesh_Krishnan on 2015-07-18
I've downloaded printer driver for canon LBP 2900 B. How to install it?

---

### Post by dino99 on 2015-07-18
check that the package 'printer-driver-cjet' from the ubuntu archive is installed

CJET filters printer data from stdin to stdout, converting HP PCL (Printer Command Language) escape sequences and data structures, e.g. font headers,
to their CaPSL equivalents.

CaPSL stands for Canon Printing System Language.  It is a set of control command developed for the Canon European Language Printer. CaPSL was used
in Canon Export Models such as LBP-8markIII series and LBP-4series.
Canon's older Japanese models (LBP-A404 GII etc. LIPS-III as default command) usually have CaPSL emulation mode.

---

### Post by Bucky Ball on 2015-07-18
*Thread moved to **General Help**.*

That printer doesn't look very compatible with Ubuntu. 

[http://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp2900b.aspx?type=drivers&language=EN&os=Linux%20%2864-bit%29](http://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp2900b.aspx?type=drivers&language=EN&os=Linux%20%2864-bit%29)

Generally Canon is fairly friendly. Is this a very new model?

PS: You could try installing printer-driver-cjet but doubt it has anything to do with this. When/if it does nothing, uninstall as it may confuse things later.

The main question is: Where did you download a Linux driver for this device???

---

### Post by monkeybrain20122 on 2015-07-18
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

That printer doesn't look very compatible with Ubuntu. 

[http://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp2900b.aspx?type=drivers&language=EN&os=Linux%20%2864-bit%29](http://www.canon-europe.com/support/consumer_products/products/printers/laser/i-sensys_lbp2900b.aspx?type=drivers&language=EN&os=Linux%20%2864-bit%29)

The main question is: Where did you download a Linux driver for this device???

Sorry missed the fine print.

---

