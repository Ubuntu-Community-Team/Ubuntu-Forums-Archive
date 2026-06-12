---
title: "Lexmark E332n Printer Problem"
date: 2008-07-02
forum: General Help
---

### Post by gus_zernial on 2008-07-02
I'm setting up a Lexmark E332n printer on Kubuntu 8.04 Hardy.
Lexmark provides drivers for this printer in a debian package
print-drivers-linux-glibc2-x86.deb, which I installed sucessfully.
This in turn provides a Lexmark Print Drivers setup utility which 
I used sucessfully to install my Lexmark E332n.

The problem is, I can't print to it - the print requests seem
successful but nothing comes out. For example, 

$ sudo lp -d E332n xorg.conf
request id is E332n-17 (1 file(s))

No printout, then I do

$ lpq -P E332n
E332n is ready
no entries

When I request the print, /var/log/messages and /var/log/dmesg 
show nothing. If I tail /var/log/cups/access_log I get:

localhost - - [02/Jul/2008:14:38:03 -0500] "POST / HTTP/1.1" 200 416 CUPS-Get-Classes successful-ok
localhost - - [02/Jul/2008:14:38:03 -0500] "POST / HTTP/1.1" 200 181 Get-Jobs successful-ok
localhost - - [02/Jul/2008:14:38:03 -0500] "POST /printers/E332n HTTP/1.1" 200 3760 Print-Job successful-ok

This is a network printer and I can print to it from other systems.
I can also print a test page from the printer itself.

Appreciate ideas to diagnose and/or resolve.

-

---

