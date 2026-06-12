---
title: "Desperation-Delete network-manager by mistake"
date: 2015-11-02
forum: General Help
---

### Post by hoboy on 2015-11-02
I have delete network-manager  by mistake how can I reinstall it using live ubuntu dvd ?

---

### Post by grahammechanical on 2015-11-02
In System Settings>Software & Updates>Other Software tab you can set the CD as a software source or repository. The boxes should already be present but unchecked. Then Software Centre should be able to install Network Manager from the CD or DVD disk which it actually is.

After Network Manager is installed uncheck those boxes otherwise every time you load Software Centre you will be nagged to insert the CD into the drive.

Regards.

---

### Post by Bucky Ball on 2015-11-02
*Thread moved to **General Help**.*

---

### Post by hoboy on 2015-11-02
do you mean that <Other Software tab you can set the CD as a software source or repository> I should click on Other Software ?
this place is empty, but the dvd is under Ubuntu Software tab.

---

### Post by Bucky Ball on 2015-11-02
Then make sure it is ticked and enabled as a repository, close Software and Updates so the machine updates and includes the new DVD repo (this may take a little bit), once that's finished, go to SCentre and install network manager. :)

---

### Post by hoboy on 2015-11-02
ok I am out live dvd but still when I click on any app from Software Center to install the install button is not active.

---

### Post by hoboy on 2015-11-02
when I used sudo apt-get update I get failed to fetch all the the url with http:// 
I am very desperate

---

### Post by HermanAB on 2015-11-02
Well, first get the network to work and then install network manager:

$ ifconfig
(to see what the network device is called)

$ sudo dhclient em1 
(or whatever it is called, to get an IP address)

Now install:
$ sudo apt-get NetworkManager

---

### Post by hoboy on 2015-11-03
When I $ sudo dhclient em1 
I get the following error:
Cannot find device em1

---

