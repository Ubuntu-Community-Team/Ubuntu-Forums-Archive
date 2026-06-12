---
title: "cannot sutdown / suspend  PC restart 3 sec automatically"
date: 2016-02-11
forum: General Help
---

### Post by jkdyzrexkngb on 2016-02-11
Hi
I have this computer for 5 years and I have these problems been a year and a half on my desktop computer

1 issue) sometime I cannot shutdown by (graphic from desktop), (TTY sudo shutdown now -h) or from (desktop through terminal sudo shutdown now -h)

it hang on different stages of the shutting down process, rarely is the same step
I don't get an error message just hang shutting down.


2 issue) sometime if I just want to suspend but the computer restart by itself 3 seconds later for no apparent reason

by coincidence
lately I started shutting down the router that this PC is connected to with a cable
today I turned on the router so I can use my wifi phone
suddenly the computer turned on by itself

so I suspend the computer and it started 3 sec again
I shutdown the router, suspend my computer and it does not restart
I did this multiple times and every time it gave the same results as above

conclusion
when router is on, suspend restart after 3 sec
when router is OFF, computer DOES NOT restart and goes into suspend

BIOS never was configured in anyway to WOL any NIC
ROUTER never was configured in anyway to WOL any NIC


uanme -a:
Linux 4.2.0-29-generic #34-Ubuntu SMP Mon Feb 8 16:57:47 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)


can anyone shed a light on this and how can I fix it

---

### Post by furtom on 2016-02-12
> **jkdyzrexkngb said:**
> Hi
I have this computer for 5 years and I have these problems been a year and a half on my desktop computer

1 issue) sometime I cannot shutdown by (graphic from desktop), (TTY sudo shutdown now -h) or from (desktop through terminal sudo shutdown now -h)

Sometimes 
```
sudo shutdown -h now
```
is not enough to bring the system to power off. Try:
```
sudo shutdown -hP now
```

In my system, I need the -P option to power off, the -h will just halt and wait for the user to push the button.

Also, I don't know if it's a typo, but if you actually entered what you wrote, sudo shutdown now -h, that would be wrong. The options go before the time argument.

See the [man page]("http://linux.die.net/man/8/shutdown") for more info.

---

### Post by jkdyzrexkngb on 2016-02-13
yeah it was a typo about shutdown now -h


the issue is I cannot shut it down from the graphic either


*** what do you think about my 2nd issue

I can suspend the computer but only if the router is off, and when I turn on the router
the computer start automatically..

---

### Post by jkdyzrexkngb on 2016-02-23
adding information:
When I  disable network manager eth0 connection, computer does not resume after  suspend..so there is something with network that make computer resume  immediately after suspend

---

