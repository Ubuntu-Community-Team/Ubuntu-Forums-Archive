---
title: "&quot;There was a problem connecting to the CUPS server.&quot;"
date: 2015-02-27
forum: General Help
---

### Post by arie_maron on 2015-02-27
I am using Ubuntu 14.10 

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

with the Unity shell.
When I try to access a network Printer that I have (HP OfficeJet 6500A) through System Settings -> Printers then right clicking the printer and selecting Properties, View Print Queue or any other option I get the response "There was a problem connecting to the CUPS server.".

I am able to send jobs to print on this printer and can access and manage it through a browser using "http://localhost:631" and can verify that my computer recognizes the printer , for instance:

 arie@ubuntu1:/var/log/cups$ lpinfo -v
network socket
serial serial:/dev/ttyS0?baud=115200
network lpd
network http
network ipp
network https
network ipps
direct hp
network ipp14
direct parallel:/dev/lp0
direct hpfax
network dnssd://Officejet%206500%20E709a%20%5B145954%5D._pdl-datastream._tcp.local/
network socket://192.168.1.107:9100

It seems that the issue is only with the GUI itself.
In "/var/logs/cups/accesss_log" file I can see that the GUI connected to CUPS with entries such as "localhost - - [27/Feb/2015:12:55:02 +0200] "POST / HTTP/1.1" 200 273 Create-Printer-Subscriptions successful-ok" appearing every time I try to use the GUI.

---

