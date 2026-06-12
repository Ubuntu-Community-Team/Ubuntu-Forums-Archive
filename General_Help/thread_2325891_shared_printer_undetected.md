---
title: "shared printer undetected"
date: 2016-05-26
forum: General Help
---

### Post by gianluca3 on 2016-05-26
Hello,

stupid problem here but is keeping me blocked...

I have a printer connected with a USB cable to pc-A (ubuntu 16.04). It works fine.

pc-B (ubuntu 16.04) is connected on the same network, actually under the same hub. pc-B sees some 15 printers in the offices around but not the one under pc-A.

From pc-B I can ssh to pc-A without problem.

What am I missing?

best and thanks in advance
g.

---

### Post by wyliecoyoteuk on 2016-05-31
Assuming the other PCs are running Windows:
Have you got Samba server installed and configured on PC-A?
Is the printer shared?

---

### Post by gianluca3 on 2016-06-13
thanks for the reply. 

i was out of office, i finally came and checked, yes samba server is there and the printer is shared..

??

best
g.

---

### Post by SeijiSensei on 2016-06-13
You don't need samba for this.

By default, CUPS only listens on the localhost interface for security reasons.  To allow remote access to the printer, on pc-A replace the line
```
Listen localhost:631
```
in /etc/cups/cupsd.conf with
```
Listen *:631
```
then restart CUPS with "sudo service cups restart".  Now on pc-B, point a browser at [http://localhost:631/](http://localhost:631/) and choose Administration > Add Printer.  Enter your login username and password when prompted. See if the printer now appears.

---

### Post by gianluca3 on 2016-06-23
dear SeijSensei,

thanks a lot for your reply. Sorry for my late reply, various problems beyond the printers. I had to make a fresh install again and then I correctly configured the server with these indications:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

now it works fine

thanks
g.

---

