---
title: "Unable to locate package"
date: 2023-04-18
forum: General Help
---

### Post by stevermann on 2023-04-18
I upgraded from Ubuntu 18 to 22. When  tried to install nala, I get "Unable to locate package"


Any ideas how to fix tis?


steve@NUC:~$ sudo apt-get install nala
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nala

[Ubuntu – Package Search Results -- nala]("https://packages.ubuntu.com/search?suite=jammy&section=all&arch=any&keywords=nala&searchon=names") shows it is available.

---

### Post by Bashing-om on 2023-04-18
stevermann; Hello -

Yeah nala is available:
> 
sysop@x2204mini:~$ apt list nala
Listing... Done
nala/jammy-backports,jammy-backports 0.11.1~bpo22.04.1 all
sysop@x2204mini:~$ apt show nala
>>
APT-Sources: [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) jammy-[color=red]backports/universe[/color] amd64 Packages


Please insure that you have the universe and backports repositories enabled in your sources.

[INDENT]Hope this helps
[/INDENT]

---

