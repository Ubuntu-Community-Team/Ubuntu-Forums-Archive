---
title: "bluetooth"
date: 2007-02-24
forum: General Help
---

### Post by Rhaddad on 2007-02-24
Hello,
my dell inspiron 9400's bluetooth, doesent work. I have tried installed the OBEX Client and all, but it just does not detect any devices.

---

### Post by reclusivemonkey on 2007-02-24
> **Rhaddad said:**
> Hello,
my dell inspiron 9400's bluetooth, doesent work. I have tried installed the OBEX Client and all, but it just does not detect any devices.

Have you installed bluez?

---

### Post by RudolfMDLT on 2007-02-24
Hi,

could you post back with some info for me and I'll try to help?

what are you running K\Ubuntu 6.0?

also, open up the terminal and type in 

lsmod | grep bluetooth

before I plug in my usb dongle I get this:
bluetooth              53476  4 rfcomm,l2cap

and after it has been plugged in and setup:
bluetooth              53476  13 [COLOR="Red"]hci_usb[/COLOR],rfcomm,l2cap

We need to see whether the hardware gets loaded.

Cheers,

Rudolf

---

