---
title: "Have 2 netowrk cards and no internet"
date: 2007-05-20
forum: General Help
---

### Post by desertboy on 2007-05-20
I've got an onboard network card and a seperate cheap pci network card in my pc, I've after a lot of heartache managed to get ubuntu installed (8800gts Nvidia card caused me lots and lots of woes). I desperately want this working because I've been using vista for a month and it's wrong. 

Vista can't see my onboard ethernet which is why I have a pci one to connect my cable modem to. I've tried plugging the cable modem into both network cards to no avail. When I run ifconfig -a it repots eth0, but no data transfer any ideas. How could I identify which network card it's seeing short of removing the pci one.

My pci network card reports as rtl8139-d  in device manger in vista.

Running edgy because fiesty won't boot, using Vista (spit) to post as I've no other way of connecting to the internet.

---

### Post by rich.bradshaw on 2007-05-20
whats the output of lspci and lsusb?

If you don't realise. you can type:

lspci > lspci.txt

to get the output of the command into a text file - saves you typing it out...

---

