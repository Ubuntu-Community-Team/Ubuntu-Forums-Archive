---
title: "Problems compiling libmodbus 3.0.6"
date: 2015-10-12
forum: General Help
---

### Post by UkMeterman on 2015-10-12
I am finding that libmodbus [http://libmodbus.org/](http://libmodbus.org/)  is compiling incorrectly on both my laptop and desktop running Ububtu  14.04 both were upgraded from 11.10 some time ago. I have tried using  the live CD version of 14.04 and it compiles fine.
  To reproduce the problem download and unpack 3.0.6 edit  /tests/unit-test-server so that it is using a valid serial device on  your pc look for /dev/ttyUSB0

  ./configure
make cd tests sudo ./unit-test-server rtu
  on my pc I am getting an ERROR connection reset by peer:read  message 
  Any suggestions?

---

