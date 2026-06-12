---
title: "efax unable to send/receive calls"
date: 2007-05-18
forum: General Help
---

### Post by jmvidalvia on 2007-05-18
I installed efax and efax-gtk

My lspci shows this modem:
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

I also installed sl-modem-daemon
I do: sudo /etc/init.d/sl-modem-daemon start

But efax-gtk says:

jm@jm:/etc$ efax-gtk
Socket running on port 9900
efax-0.9a: 35:57 opened /dev/modem
efax-0.9a: 35:59 using modem:1 in class 1
efax-0.9a: 35:59 dialling T555555555
efax-0.9a: 36:02 Error: dial command failed

¿any idea about where should I check?
Thanks a lot!

---

