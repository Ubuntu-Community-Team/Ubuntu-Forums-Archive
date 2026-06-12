---
title: "How to edit MBR? Wubi U. + another  distro"
date: 2008-07-02
forum: General Help
---

### Post by nooby on 2008-07-02
I want to add to the mbr that WUBI created other distros 
that are frugal mounted. I mean programs like Puppy. 

They need to do a grub but Wubi have alread written a MBR 
if I get it? 

> In XP's MSCOFIG/BOOT>INI, there it sits:
(Wubildr.mbr="Ubuntu")

How do I add puppy there and Linux Mint and PcLinux and so on?

Here is how my boot.ini looks like 

> [boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"



How do I write in Puppy there?

---

### Post by ago on 2008-07-03
wubildr.mbr is a customized grub4dos that only loads ubuntu

but you can use grub4dos instead and create an appropriate menu.lst (for the menu.lst needed for wubi see c:\ubuntu\winboot)

you will then have 2 boot menus, the windows menu will point to grub4dos which will show you a second menu with the other options

---

