---
title: "CUPS-PDF LPD Printer Blank Pages"
date: 2016-07-02
forum: General Help
---

### Post by keith_s2 on 2016-07-02
Hello,

I'm trying to submit a job to a CUPS-PDF pritner on Ubuntu 14.04 via the LPD protocol (needed at the moment). The server takes and accepts the job, as well as generates output. However... that output is simply a cover sheet with no actual content on it.

I tried the solution of changing out the printer driver with one that was manually selected via the "Modify Printer" interface within the CUPS Administration Panel, however that did not work past actually getting the cover page to show up. I ran cupsdisable MY-PDF-PRTR, and used lpstat -o to see if it was getting the input, and then viewed the spooled input using nano. The input needed is in that file, but it is not being copied onto the actual PDF itself. I also need to know how to disable that cover sheet, if at all possible.

Thanks!

---

### Post by keith_s2 on 2016-07-04
Bump. I found out that IPP works fine, but it's just LPD acting up. Unfortunately, for the project that I'm working on, LPD is a necesity.

---

