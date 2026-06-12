---
title: "Recommend me  a laser printer for 9.10"
date: 2013-04-10
forum: General Help
---

### Post by berniedd on 2013-04-10
Running 2 desktops in the office with Ubuntu 9.10 and an HP Laserjet 1200. One connects to the printer with parallel port cable, the other connects via USB. The Laserjet has given up the ghost, and we'd like to get a new basic cheap current laser printer that is perfectly compatible with these 2 desktops. Support for the OS is of course expired, and we'd like to connect a printer that will work right out of the box and  not give us any driver headaches. The desktops work just fine, have 512 MB RAM, are at least 7 years old, and are connected to the Internet via a router.  We are  not inclined to upgrade to a more recent Ubuntu version, what with the serious hardware limitation of these desktops. Also, how to connect the new printer to 2 desktops? All printers I see are single-USB port nowadays. Thanks for any help, guys.

---

### Post by Impavidus on 2013-04-10
You can print via the network, with the printer attached to one of the machines: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
This requires the computer to which the printer is attached to be switched on to allow both computers to print.

With that old hardware you should still be able to run the latest Lubuntu.

---

### Post by mörgæs on 2013-04-10
> **berniedd said:**
> We are  not inclined to upgrade to a more recent Ubuntu version, what with the serious hardware limitation of these desktops.

You should. Lubuntu 12.10 runs on almost everything if it has 512 MB memory.

---

### Post by berniedd on 2013-05-01
Thanks, Impavidus.  I assume your printers are network printers, with LAN sockets. 

I have seen an office colleague set up where he can print from his laptop connected by wifi to the network,  to the printer that's connected by ordinary USB to a desktop on the LAN.  That system runs Windows7. How can I do it with our setup described above (Ubuntu 9.10) with the 2 desktops connected to the router? That way, I can make do with an ordinary printer and not have to get a network printer.

---

### Post by Bucky Ball on 2013-05-01
Running 9.10 in an office environment, where I presume the computers are online, is a very bad idea. That release hasn't had updates, including security updates, in two years. 

Go Lubuntu upgrade or stick another 512 RAM in each machine and run 12.04 LTS of another flavour. If you don't like Unity try Xubuntu. You should be running an LTS release for production machines in any case.

---

### Post by Impavidus on 2013-05-01
> **berniedd said:**
> Thanks, Impavidus.  I assume your printers are network printers, with LAN sockets. 

I have seen an office colleague set up where he can print from his laptop connected by wifi to the network,  to the printer that's connected by ordinary USB to a desktop on the LAN.  That system runs Windows7. How can I do it with our setup described above (Ubuntu 9.10) with the 2 desktops connected to the router? That way, I can make do with an ordinary printer and not have to get a network printer.

I was talking about ordinary USB printers, which are connected to a host, not to the network directly. The link I gave you describes how to set up the situation you want: a printer connected by USB to a desktop on a LAN. I never tried it myself though, as I hardly ever print so I didn't bother.

But indeed, try a recent Lubuntu or get extra RAM and try Xubuntu 12.04 LTS. Having not updated for two years means you have programs, especially your web browser, with security leaks.

---

### Post by SeijiSensei on 2013-05-01
In response to your original question, [Brother]("http://www.newegg.com/Laser-Printers/BrandSubCat/ID-1816-630") provides good Linux support for their printers, and they are reasonably inexpensive but robust.

---

