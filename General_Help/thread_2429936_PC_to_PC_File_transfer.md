---
title: "PC to PC File transfer"
date: 2019-10-25
forum: General Help
---

### Post by pushbike06 on 2019-10-25
Just wondering. In the "old days" we could do a PC to PC file transfer (Dos system) using I think Norton Commander and a RS232 cable.
Is it possible to do a PC to PC file transfer (Ubuntu system) using a USB cable? That is, cut out the middle man (USB stick).

---

### Post by Holger_Gehrke on 2019-10-25
Yes and no. USB is designed as a tree with one host (the PC) and lots of devices. There are devices (smart phones and tablets, mostly) which can act as a host if they detect a special kind of cable (USB on the go). And there are "cables" which actually have some kind of device either as a bulge in the middle or in one of the plugs; with these both hosts communicate with the device which reformats the data to look like it's coming from a device and pushes it to the other PC. AFAIK there are drivers in the LINUX kernel for these kind of things, but I don't own one of them and have never tried it.

On the other hand, network ports are ubiquitous on modern PCs. Just use a simple network cable, set up server software on one of the two (nfs, samba, ... ) and off you go.

Holger

---

### Post by SeijiSensei on 2019-10-25
> **Holger_Gehrke said:**
> On the other hand, network ports are ubiquitous on modern PCs. Just use a simple network cable, set up server software on one of the two (nfs, samba, ... ) and off you go.
Or just install openssh-server on both machines and use SCP, SFTP, or rsync.

---

### Post by HermanAB on 2019-10-25
Ayup, ssh or netcat over ethernet can do that.

---

