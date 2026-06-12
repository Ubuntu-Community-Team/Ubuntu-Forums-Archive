---
title: "Skype doesn´t start"
date: 2013-11-09
forum: General Help
---

### Post by broodjeparkiet on 2013-11-09
I have installed skype using the software center but it won´t start nothing happens when i start it i already reinstalled without succes and i am running a fresh instrall of ubuntu 13.10

When i type dpkg -l skype in terminal i get this:


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  skype          4.2.0.11-0ub amd64        client for Skype VOIP and instant

---

### Post by rclocher3 on 2013-11-11
Hi, I was having a similar problem also.  Skype was working under Ubuntu 13.04 Raring Ringtail for me, but when I upgraded to Ubuntu 13.10 Saucy Salamander, Skype wouldn't start.  My computer has a 32-bit microprocessor.

You should try to run Skype from the command line, because when the program fails there will be an error message.  Press Ctrl+Alt+T to get a terminal, and then type "skype<Enter>".  The problem I had caused the error "Segmentation fault (core dumped)".

If you type another command at the terminal you can discover which version of Skype you have.  To find out, run "dpkg -l skype" .  The version I had was 4.1.0.20-1.

I downloaded version 4.2.0.11-1 using the instructions in this web page:
[http://www.tecmint.com/skype-4-2-released-install-on-ubuntu-debian-linux-mint-and-fedora/](http://www.tecmint.com/skype-4-2-released-install-on-ubuntu-debian-linux-mint-and-fedora/)
and I am happy to say that the new version seems to work for me.

Good luck to you!

---

