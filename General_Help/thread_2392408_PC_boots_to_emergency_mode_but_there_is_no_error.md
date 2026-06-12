---
title: "PC boots to emergency mode but there is no error"
date: 2018-05-21
forum: General Help
---

### Post by 1nikolas on 2018-05-21
Hi I opened my pc yesterday and I saw that it was booting to emergency mode. I saw all the errors from systemctl --failed and I fixed them all (there were some errors with mounting windows disks and some that I didn't understand but I fixed them all). Now it keeps booting to emergency mode although systemctl --failed prints no errors. What is going wrong? Thanks in advance!
(I have Ubuntu 16.04 LTS)

---

### Post by cruzer001 on 2018-05-21
Emergency mode reverts you back to the generic graphic driver.  Could your current install driver have failed?

Check your kernel log for errors (the last 20 or so lines).
/var/log/kern.log

Did you update yesterday?  Try dropping back to previous kernel at the boot screen>advance options.

---

