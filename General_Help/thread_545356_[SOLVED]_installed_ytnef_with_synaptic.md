---
title: "[SOLVED] installed ytnef with synaptic"
date: 2007-09-07
forum: General Help
---

### Post by DarinB on 2007-09-07
i installed ytnef with synaptic opened thunderbird clicked winmail.dat open with opened terminal and added ytnef -f . winmail.dat then got this error

darin@darin-desktop:~$ ytnef -f . winmail.dat
ERROR processing file

what am i doing wrong

---

### Post by unique_stephen on 2007-10-04
ytnef gives this message if it was not handed a file to open.
Try saving the winmail.dat file to the desktop
change directory to the desktop, i.e,$ cd ~/Desktop
and open the file using $ ytnef -F -f . winmail.dat

The attachment should now be on the desktop. That said there are some attachments that I get sent to me from my boss using outlook on a mac that I cant open.

---

