---
title: "Long boot time after installing ubuntu"
date: 2014-04-14
forum: General Help
---

### Post by elo96 on 2014-04-14
I recently installed ubuntu on my PC, and since the installation have found that there is a delay of approximately 180s before the motherboard beeps to indicate that it is loading and the mb splash screen appears. I've tried boot repair, which provided information here: [http://paste.ubuntu.com/7251212/](http://paste.ubuntu.com/7251212/). Should Grub be installed on sda1?

---

### Post by ajgreeny on 2014-04-14
The motherboard beeps happen before any OS software has been loaded or run; that is the POST beep to tell you if the hardware is OK or faulty in some way, with different beep patterns for different problems.

I suspect whatever you are seeing or hearing now is coincidental to the installation of ubuntu.

---

### Post by elo96 on 2014-04-30
In case anyone else stumbles across this: I ended up clearing the RTC RAM, which seems to have alleviated the problem.

---

