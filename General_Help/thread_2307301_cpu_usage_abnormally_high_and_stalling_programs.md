---
title: "cpu usage abnormally high and stalling programs"
date: 2015-12-23
forum: General Help
---

### Post by chkneater on 2015-12-23
Hi, I am using 12.04 Ubuntu ATM and started noticing that Clementine was stalling and would not respond whenever the screensaver came on... I resolved it by turning off the screensaver, but then I noticed that it would still stall out whenever I opened Firefox.  So I opened up Task Manager to see what was going on and noticed that RAM usage was pretty low but the CPU would fly thru the roof on and off frequently.  I had Clementine up and running and playing then opened Firefox at which Clementine stalls.  I noticed the CPU was maxed, but when I killed Clementine the cpu was still at half. I killed Firefox and usage was still abnormally high.  Looking thru task manager there was a line

" /usr/bin/X  :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none " 

it was using from 3 to 25% of the cpu up and down.  I know that this has something to do with the cpu prob, but I don't know what else is involved.

Any ideas on fixes IN B4 "UPGRADE"; this is very unusual?

---

### Post by chkneater on 2015-12-25
apparently lightDM had lost its settings during an update and reinstalling gdm seems to have helped some, not sure it's fixed entirely...

anyone ELSE have any ideas??

---

### Post by Bucky Ball on 2015-12-25
*Thread closed. *

Seeing as you've started a duplicate that is getting some action.

In future, please do not post duplicates or near-duplicate threads. If your thread has not seen action for twelve or so hours, simply post 'bump'. Thanks.

---

