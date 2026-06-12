---
title: "obexftp and irda?"
date: 2005-06-08
forum: General Help
---

### Post by burlap on 2005-06-08
I would like to try obexftp with irda before I am forced to buy a bluetooth dongle. 

Does anyone had any success with it? 

I am using siemens s65 phone, it is attached to irda port (multisync works, or at least some parts of multisync work). 

this is (a part of) irdadump output:```

09:36:39.607422 xid:cmd e75b585b > ffffffff S=6 s=0 (14)
09:36:39.697306 xid:cmd e75b585b > ffffffff S=6 s=1 (14)
09:36:39.787302 xid:cmd e75b585b > ffffffff S=6 s=2 (14)
09:36:39.877269 xid:cmd e75b585b > ffffffff S=6 s=3 (14)
09:36:39.967258 xid:cmd e75b585b > ffffffff S=6 s=4 (14)
09:36:40.057243 xid:cmd e75b585b > ffffffff S=6 s=5 (14)
09:36:40.142250 xid:rsp e75b585b < 08364000 S=6 s=5 SIEMENS S65 hint=b124 [ PnP Modem Fax IrCOMM IrOBEX ] (28)
09:36:40.147256 xid:cmd e75b585b > ffffffff S=6 s=* driftwood hint=0400 [ Computer ] (25)
```obexftp gives the following errors:```
$obexftp -i -l /
No custom transport
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
Connecting...failed: connect
Still trying to connect
```I have found somewhere (openobex, multisync or opensync list, I I can't find, sourceforge is down at the moment) that it seems that whatever the options, obexftp tries to use bluetooth interface, not irda. So I have followed this information and also straced obexftp. This may be the relevant part, complete output is attached:```
write(2, "Connecting...", 13)           = 13
socket(PF_BLUETOOTH, SOCK_STREAM, 3)    = 4
bind(4, {sa_family=AF_UNSPEC, sa_data="\0\0\0\0\0\0\0\0\0\0\0\0\0\0"}, 10) = -1 EINVAL (Invalid argument)
close(4)                                = 0
socket(PF_BLUETOOTH, SOCK_STREAM, 3)    = 4
bind(4, {sa_family=AF_UNSPEC, sa_data="\0\0\0\0\0\0\0\0\0\0\0\0\0\0"}, 10) = -1 EINVAL (Invalid argument)
close(4)                                = 0
write(2, "failed: connect\n", 16)       = 16
write(2, "Still trying to connect\n", 24) = 24
```
Is it possible at all to use irda with obexftp? (I know it is slow, but I want to know if it works **at all**). What is the better solution: cable or bluetooth (considering both multisync/opensync and obexftp)?

---

### Post by burlap on 2005-06-09
I compiled obexftp from sources (source package) without bluetooth and it works with irda. So I have filed [a bug](https://launchpad.ubuntu.com/malone/bugs/970).

---

### Post by pyronicte on 2005-11-26
Have you tried obextool? It's great as GUI for obexftp

---

