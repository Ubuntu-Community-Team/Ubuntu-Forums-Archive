---
title: "Ubuntu 14.04 gcc build problems"
date: 2015-10-13
forum: General Help
---

### Post by UkMeterman on 2015-10-13
Hi,
I have been having problems building libmodbus 3.0.6 [http://libmodbus.org/](http://libmodbus.org/) it builds correctly on a 14.04 live cd system, but both my laptop and desktop running 14.04 have problems. How do I get my GCC install including any configuration to the same same as the live CD? 

To reproduce download and unpack 3.0.6.
 ./configure
 make
cd tests
./unit-test-server rtu

you make need to edit unit-test-server.c so that it uses a serial device on your system

A valid response would be waiting for an indication 

I am also getting ERROR connection reset by peer : read  

Thanks

---

