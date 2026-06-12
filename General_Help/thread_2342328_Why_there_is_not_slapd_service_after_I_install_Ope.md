---
title: "Why there is not slapd service after I install OpenLDAP"
date: 2016-11-05
forum: General Help
---

### Post by sincos2007 on 2016-11-05
Hi All,

I downloaded source files of Berkeley DB and OpenLDAP. Then I compiled and installed them. I do:

 $make depend

$make

$make test (successfully)

$make install

$ service slapd
slapd: unrecognized service

Thanks

---

### Post by kevdog on 2016-11-05
What version of ubuntu are your running?  service commands were for upstart which was on 14.04 and systemd command 16.04 are different --- ie
sudo systemctl enable slapd.service
sudo systemctl start slapd.service

First command makes it load a boot everytime, second command just starts the service if you don't want to reboot.  systemctl is the command line tool to start,stop, restart services under systemd

---

### Post by sincos2007 on 2016-11-06
$sudo systemctl enable slapd.service
Failed to execute operation: No such file or directory

I use Ubuntu16.04

---

