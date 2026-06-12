---
title: "HOWTO: Print through an SMC Barricade Router Model # 7004ABR (750.5432) on Ubuntu 7.1"
date: 2007-11-08
forum: General Help
---

### Post by Muki on 2007-11-08
Thanks to [http://www.cadvision.com/blanchas/Intro2dcRev2/pagecups.html](http://www.cadvision.com/blanchas/Intro2dcRev2/pagecups.html), from whom I paraphrased these instructions.

1. Access CUPS 1.3.2 via Firefox by typing [http://localhost:631/](http://localhost:631/)
2. From the Home Page, choose Add Printer
3. Add New Printer: choose a name
4. Device for YourPrinter: LPD/LPR Host or Printer
5. Device url: lpd://192.168.x.x/lpt1
6. Make: choose your printer make
7. Model: look for the driver for your model

You are done! Print a test page!

There is no way that I know of to fix the two extra pages that print out with each print job. If someone has a fix or a work-around, please let me know.

---

