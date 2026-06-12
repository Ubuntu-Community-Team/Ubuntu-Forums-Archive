---
title: "Cups not responding"
date: 2007-06-24
forum: General Help
---

### Post by ZBlach on 2007-06-24
Hi, I've a bit of a nagging issue after reinstalling feisty. CUPS seems to run okay (no errors with cupsd), but pointing konqueror to [http://localhost:631](http://localhost:631) just stalls out. And adding printers through the control panel just times out.

I've purged cupsys-* and reinstalled it with no effect. Any ideas?

---

### Post by mitch.c on 2007-06-26
I assume this means you don't have any printers installed... can you install a printer using lpadmin?
```
$ lpadmin -p myprinter -E -m ppd_file -v device_uri -u allow:all
```
If you need help discovering ppd_file or device_uri, reply with you printer make/model and connection type.

What is the output from:
```
$ netstat -an | grep 631
```
Is there anything in /var/log/syslog after a cupsys restart that may give us a clue?

Maybe posting /etc/cups/cupsd.conf would help?

---

### Post by el_itur on 2007-06-30
Sorry wrong thread. 
Hi, bumping because I have the same problem.

My printer is a local lpt  canon bjc1000.
I triede all four drivers with thesame resoult. the printer don't respond

Heres the print of my network
```
gandalf-desktop:~$ netstat -an | grep 631
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 201.231.51.54:9090      82.182.182.112:63159    ESTABLISHED
unix  2      [ ACC ]     STREAM     LISTENING     16315    /var/run/mysqld/mysqld.sock
unix  3      [ ]         STREAM     CONNECTED     416316   
unix  3      [ ]         STREAM     CONNECTED     416315   
unix  3      [ ]         STREAM     CONNECTED     17631   
```

---

