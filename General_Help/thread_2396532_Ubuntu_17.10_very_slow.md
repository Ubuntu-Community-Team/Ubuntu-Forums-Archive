---
title: "Ubuntu 17.10 very slow"
date: 2018-07-17
forum: General Help
---

### Post by anasali90 on 2018-07-17
Hello everybody, I bought a new laptop and I have installed Ubuntu 17.10. The problem is that Ubuntu is very slow when starting it and when I open any application - it takes for example about 13 seconds to open Google Chrome. I have tried to change the power saving setting from bios but nothing changed. Here are my laptop specifications: Lenovo, Processor: Core i7 7th Gen, Nvidia Geforce 940mx, 8 GB Ram, 1TB hard disk.
Please does anyone know what the problem is?

---

### Post by HermanAB on 2018-07-17
Well, that kind of machine should be very fast, so something is very wrong.  

First have a look at the processor and memory use with 'top'.

Chrome wants to go out on the network, so your problem could be due to a network configuration problem.  You can investigate network issues with 'ntop', 'nslookup', 'dig' and even the venerable 'telnet'.  Use nslookup and dig to see whether you have a lame DNS.

---

### Post by monkeybrain20122 on 2018-07-17
Ubuntu 17.10 will reach end of life maybe in a few days, so instead of wasting your time trouble shooting it, just do a clean install of 18.04. Don't do "upgrade" since you would definitely want to start with a clean slate instead of leaving bits of the problematic 17.10 install around, should be a no brainer since this is a new install.

---

