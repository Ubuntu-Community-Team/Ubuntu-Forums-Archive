---
title: "Hard disk issue"
date: 2017-10-16
forum: General Help
---

### Post by pivanchy on 2017-10-16
During starting my Ubuntu, I've got a message like this:

APM_level = not supported...

After some googling, I've found a few interesting commands:

$ sudo hdparm -I /dev/sda

- supported
- not enabled
- not locked
- frozen
- not expired
88 min for Security erase unit.


$ sudo hdparm -y /dev/sda
issuing standby command

$ sudo hdparm -C /dev/sda

drive state is: standby

$ sudo hdparm -B 127 /dev/sda

setting Advanced Power Management level to ox7f (127)

SG_IO: bad/missing sense data, sb[]: 70 00 05 00 00 00 00 0a 04 51 40 7f 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
APM_level = not supported


What happened with my HD?

---

### Post by Frogs Hair on 2017-10-16
Don't know if the link is applicable. 

[https://askubuntu.com/questions/768373/hard-drive-error-bad-missing-sense-data](https://askubuntu.com/questions/768373/hard-drive-error-bad-missing-sense-data)

---

### Post by pivanchy on 2017-10-16
So it worked fine, but after reboot, it stopped to work.

---

### Post by oldos2er on 2017-10-16
Thread moved to *General Help*

---

### Post by pivanchy on 2017-10-21
Any updates on this?

---

