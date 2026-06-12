---
title: "Graphical Bluetooth Program"
date: 2006-11-02
forum: General Help
---

### Post by Sethro on 2006-11-02
Hi everyone I have been trying to get bluetooth to work for some time now, but no luck. I really want to get it working so I can transfer stuff to and from my phone. Is their a graphical program that will set up and install bluetooth stuff. Iam terrible at fiddling around with the terminal.


Please help me out

Thanks

---

### Post by sabitha on 2006-11-02
just install gnome-bluetooth, obexserver and obexftp
if u wanna send file to your phone put launcer to your dekstop with command gnome-obex-send drag and drop the file u want transfer to that launcer. if u wanna receive the file for phone acktivate bluetooth with Application>Accesories>Bluetooth file sharing
hope thats help

---

### Post by Sethro on 2006-11-02
> **sabitha said:**
> just install gnome-bluetooth, obexserver and obexftp
if u wanna send file to your phone put launcer to your dekstop with command gnome-obex-send drag and drop the file u want transfer to that launcer. if u wanna receive the file for phone acktivate bluetooth with Application>Accesories>Bluetooth file sharing
hope thats help

Hi I installed everything that you said, but when I click on Bluetooth file sharing nothing happens. And I noticed that the bluetooth light is off. How would I enable this in Ubuntu, in Windows I would just use the thinkpad software.


Thanks

---

### Post by sabitha on 2006-11-03
do you have rfcomm and l2cap in your modules. if u dont have ir add with
$ sudo modprobe rfcomm
$ sudo modprobe l2cap

---

### Post by Sethro on 2006-11-03
Nope still no luck nothing happens...

---

