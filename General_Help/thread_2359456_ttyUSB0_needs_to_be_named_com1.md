---
title: "ttyUSB0 needs to be named com1"
date: 2017-04-24
forum: General Help
---

### Post by purplemaster78 on 2017-04-24
I have an old ms-dos .exe file that i have running and working using dosbox.  I have also changed the dosbox.conf file serial 1 from dummy to directserial realport:ttyUSB0. Upon opening of dosbox it does show that it opens the serial port. But the software I am using does not communicate with the hardware i am using. We believe that this might be due to the software having specifics instructions to just read from the com1 port. Is there a way to get either thru a symlink or some other method dosbox to actually mark the ttyUSB0 as com1

---

