---
title: "samba start - failed"
date: 2013-10-12
forum: General Help
---

### Post by Marchello_Lippi on 2013-10-12
Hi all, 

I got error when tried to start samba: 

user@host / $ sudo service samba start
[FAIL] Starting Samba daemons: nmbd failed!


Here is my /etc/samba/samba.conf : 

[global]
workgroup = SIMPLE

[test]
comment = test_only
path = /export/samba/test
read only = no
guest ok = yes


Yes, path directory exists: 

user@host / $ cd /export/samba/test
user@host /export/samba/test $ 


Right for this directory seems ok: 

user@host / $ sudo chmod 777 /export/samba/test
user@host / $ 



I can see errors in logs: 


user@host / $ less /var/log/samba/log.nmbd 

[2013/10/12 12:47:22,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.6 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/10/12 12:47:22,  0] nmbd/nmbd.c:865(main)
  error opening config file
[2013/10/12 12:49:44,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.6 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/10/12 12:49:44,  0] nmbd/nmbd.c:865(main)
  error opening config file
[2013/10/12 12:49:50,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.6 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/10/12 12:49:50,  0] nmbd/nmbd.c:865(main)
  error opening config file
[2013/10/12 12:57:34,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.6 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/10/12 12:57:34,  0] nmbd/nmbd.c:865(main)
  error opening config file




user@host / $ less /var/log/samba/log.smbd 

[2013/10/12 11:25:20.787474,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2013/10/12 11:38:21.149287,  0] printing/print_cups.c:110(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2013/10/12 11:38:21.150521,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2013/10/12 11:51:21.623805,  0] printing/print_cups.c:110(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2013/10/12 11:51:21.625045,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2013/10/12 12:04:21.921586,  0] printing/print_cups.c:110(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2013/10/12 12:04:21.922822,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2013/10/12 12:17:22.333710,  0] printing/print_cups.c:110(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2013/10/12 12:17:22.334959,  0] printing/print_cups.c:487(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL


What should I do to solve it? 
Thanks ahead.

---

