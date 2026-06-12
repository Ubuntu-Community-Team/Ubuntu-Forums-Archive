---
title: "Driverless Printing and Scanning"
date: 2023-09-25
forum: General Help
---

### Post by daniell59 on 2023-09-25
I would appreciate it if somebody could explain to me what driver less printing and scanning is. In spite of reading about it, I just cannot comprehend it.

Thanks

---

### Post by MAFoElffen on 2023-09-25
Basically Linux is very similar under the covers and how things work. This has been answered very well in this derivative of Ubuntu in their Distribution's User Guide... And this works the same for Ubuntu and it's flavors.

RE: [https://linuxmint-user-guide.readthedocs.io/en/latest/printers.html#driverless-printing-and-scanning-ipp](https://linuxmint-user-guide.readthedocs.io/en/latest/printers.html#driverless-printing-and-scanning-ipp)
> 
 **Driverless Printing and Scanning (IPP)**

 Since version 21, Linux Mint features driverless printing and scanning:
 
[LIST]
[*]Printers and scanners are detected and added automatically. 
[*]Communication with the device is done via a standard protocol called IPP. 
[*]No drivers are needed. 
[*]Installed drivers are not used. 
[/LIST]
 This standard protocol works with many devices, so for most printers  and scanners, there is nothing to do. Everything just works out of the  box.
 To print a document open File -> Print&#8230; in your application.
 
(To scan a document open Document Scanner from the application menu.)

 
This is explained in greater detail by the distribution  Ubuntu is derived from, and the branch of Linux it falls under, the Debian documentation:
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

---

### Post by Claus7 on 2024-05-05
Hello,

initially this was an issue for me as I couldn't spot the printer if is wasn't powered on. Now in noble I can go under settings->printer and it's there, even if not powered on. In the model description one can find the string: IPP Everywhere.

Regards!

---

