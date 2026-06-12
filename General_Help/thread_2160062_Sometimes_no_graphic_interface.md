---
title: "Sometimes no graphic interface"
date: 2013-07-05
forum: General Help
---

### Post by mackowiakp on 2013-07-05
I have strange problem in Lubuntu 12.04-386-LTS. From time to time (aprox 1 time per 10 laptop boots) the computer starts without graphical login interface. Only "black" ASCII console is on the screen wit text based login prompt. O course I can login and start X session manually. But it is not good solution for everyday use.

How can I resole that problem? Any idea?

---

### Post by Cheesehead on 2013-07-06
Look through /var/log/dmesg, and /var/log/syslog, and especially /var/log/Xorg.0.log for X-related or display-related error messages.

---

