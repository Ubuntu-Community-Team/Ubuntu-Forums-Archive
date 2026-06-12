---
title: "NRPE Nagios"
date: 2006-12-06
forum: General Help
---

### Post by sylvesterbeck on 2006-12-06
Hi Guys nice site and glad to see ubuntu is doing so well.

Well I have a question of course regarding nagios server monitoring with NRPE on Windows 2000/2003 via SMTp 

I have installed the NRPE client and see the service as started.
Where do I enter configuration for it 

Server name etc ?

What do I need to do to monitor CPU/DIsk Space etc or does the standard install do that for me already ?

Any help would be welcomed 

As you could have guessed I am a windows guy and only really started to linux based .

thanks

---

### Post by geep on 2007-01-24
NRPE_NT on windows works like this. ( Don't know what you mean with snmp, if you want to you integrate nagios check in cacti this is possible. )

see below for more info about nagio / cacti
[http://www.nagiosexchange.org/Charts.42.0.html](http://www.nagiosexchange.org/Charts.42.0.html)


install service nrpe_nt 

on command line ( run - cmd ) go to nrpe_nt/bin directory/nrpe_nt.exe -i

net start nrpe_nt

edit nrpe_nt.cfg file set allowed hosts. ( Add ip server )

net stop nrpe_nt
net start nrpe_nt

test on server

example

/usr/loca/nagios/libexec/check_nrpe -H &HOST

you should recive a reply

 NRPE v2.0


it works



Don't know if this is what you mean but hope it helps you. :)

---

