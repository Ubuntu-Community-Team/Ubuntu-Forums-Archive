---
title: "Please Help - Segmentation Fault affecting Python, Apt-Get..."
date: 2007-03-05
forum: General Help
---

### Post by DaRush on 2007-03-05
Please help...

Running Ubuntu 6.10 Amd 64 on a Compaq Pressario V2000 notebook.

On startup I'm alerted that there is a problem with Python.  Add/remove programs just starts then closes; Synaptic does the same thing; apt-get produces a message: segmentation faultlists 0%, and stops working tool  There are also problems with some other system tools, but everything else in the system works.  All 3rd party apps work.

Here is the relevant system log:
Mar 3 18:17:02 vlady-laptop kernel: [ 76.031466] gnome-app-insta[4784]: segfault at 0000000000000000 rip 00002ae72bfa30f0 rsp 00007fff7f134848 error 4
Mar 3 18:25:40 vlady-laptop kernel: [ 339.297670] synaptic[5156]: segfault at 0000000000000000 rip 00002b26205700f0 rsp 00007fff8d6dd9a8 error 4
Mar 3 18:32:56 vlady-laptop kernel: [ 557.427183] apt-get[5502]: segfault at 0000000000000000 rip 00002ae98024c0f0 rsp 00007fff2b051c58 error 4
Mar 3 18:33:14 vlady-laptop kernel: [ 566.568350] apt-get[5519]: segfault at 0000000000000000 rip 00002b053a7d50f0 rsp 00007fff70ac7338 error 4
Mar 3 18:34:48 vlady-laptop kernel: [ 613.542225] gnome-app-insta[5577]: segfault at 0000000000000000 rip 00002b535ec6a0f0 rsp 00007fff4c46bb78 error 4
Mar 3 18:35:01 vlady-laptop kernel: [ 620.750975] python[5606]: segfault at 0000000000000000 rip 00002b6ab93150f0 rsp 00007ffff1dc4bc8 error 4
Mar 3 18:35:02 vlady-laptop kernel: [ 620.983935] synaptic[5605]: segfault at 0000000000000000 rip 00002b1aa92d80f0 rsp 00007fff04973758 error 4

I've scanned the memory (let it run for about a day) and there were no errors.  I've scanned the file system using fsck - that made some changes, but the problem is still there.  

When I boot from a live CD this problem is not present.  Any kernel I load from my HD has the same problem though.

Does anyone have a clue what this could be caused by???  Could it be the memory, Hard Drive or something else?  Could it be Software?  Will re-installing Ubuntu :( solve the problem?

Thanks in advance....

---

