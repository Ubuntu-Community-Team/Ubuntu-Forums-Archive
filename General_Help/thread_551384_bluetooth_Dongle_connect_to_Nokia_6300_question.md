---
title: "bluetooth Dongle connect to Nokia 6300 question"
date: 2007-09-15
forum: General Help
---

### Post by moonhk on 2007-09-15
Hi 

Do you know what is my problem ?

moonhk@hex:~$ hciconfig enable
hci0:   Type: USB
        BD Address: 00:0A:94:02:68:7A ACL MTU: 310:10 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:5124 acl:73 sco:0 events:157 errors:0
        TX bytes:1918 acl:72 sco:0 commands:44 errors:0

moonhk@hex:~$ hidd --search
Searching ...
moonhk@hex:~$ hcitool dev
Devices:
        hci0    00:0A:94:02:68:7A
moonhk@hex:~$ hcitool scan
Scanning ...
        00:1C:9A:08:94:85       Nokia 6300
moonhk@hex:~$ hidd --connect   00:1C:9A:08:94:85
Can't open input device: No such file or directory (2)
moonhk@hex:~$

On the phone screen show connect failure.

moonhk

---

### Post by por100pre1 on 2007-09-15
Try sending a file:

```
gnome-obex-send -d 00:1C:9A:08:94:85 *path-of-a-file*
```

---

