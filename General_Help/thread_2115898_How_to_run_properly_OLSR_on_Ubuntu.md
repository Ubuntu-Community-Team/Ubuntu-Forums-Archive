---
title: "How to run properly OLSR on Ubuntu?"
date: 2013-02-14
forum: General Help
---

### Post by Sagan07 on 2013-02-14
Hi. I have big problem with OLSR daemon over Ubuntu/Kubuntu 12.10. I downloaded deb file from [https://launchpad.net/ubuntu/+source/olsrd/0.6.3-5](https://launchpad.net/ubuntu/+source/olsrd/0.6.3-5) , installed and trying to use it with that manuals: [http://tldp.org/HOWTO/OLSR-IPv6-HOWTO/olsrlinux.html#using](http://tldp.org/HOWTO/OLSR-IPv6-HOWTO/olsrlinux.html#using) and [http://wmunguiam.blogspot.com/2009/01/olsr-over-ubuntu-804.html](http://wmunguiam.blogspot.com/2009/01/olsr-over-ubuntu-804.html) but it not works. In my Wireshark there is no OLSR packets. Is it possible start OLSR via init.d (like quagga)? Now if I type sudo /etc/init.d/olsrd start/stop there is nothing happens. Thank you in advance for your help. Sorry for my language but English is my second language.

---

### Post by rnerwein on 2013-02-14
> **Sagan07 said:**
> Hi. I have big problem with OLSR daemon over Ubuntu/Kubuntu 12.10. I downloaded deb file from [https://launchpad.net/ubuntu/+source/olsrd/0.6.3-5](https://launchpad.net/ubuntu/+source/olsrd/0.6.3-5) , installed and trying to use it with that manuals: [http://tldp.org/HOWTO/OLSR-IPv6-HOWTO/olsrlinux.html#using](http://tldp.org/HOWTO/OLSR-IPv6-HOWTO/olsrlinux.html#using) and [http://wmunguiam.blogspot.com/2009/01/olsr-over-ubuntu-804.html](http://wmunguiam.blogspot.com/2009/01/olsr-over-ubuntu-804.html) but it not works. In my Wireshark there is no OLSR packets. Is it possible start OLSR via init.d (like quagga)? Now if I type sudo /etc/init.d/olsrd start/stop there is nothing happens. Thank you in advance for your help. Sorry for my language but English is my second language.
hi
where is your OLSR daemon placed on the system. open a terminal and type name_of_your_executable_program - if you get the answer "not found" run as super-user in / : find -name your_software
then call it with full PATH:  /etc/init.d/blablu restart or just: path_to_your_program/program start "or what ever the program needs to start"
cheers

---

